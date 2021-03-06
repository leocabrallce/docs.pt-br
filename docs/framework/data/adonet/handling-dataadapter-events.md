---
title: "Manipulação de eventos DataAdapter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 71524de2edbedb24cacc6727654aac5be0a48bb7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="handling-dataadapter-events"></a>Manipulação de eventos DataAdapter
O ADO.NET <xref:System.Data.Common.DataAdapter> expõe três eventos que você pode usar para responder às alterações feitas nos dados na fonte de dados. A tabela a seguir mostra o `DataAdapter` eventos.  
  
|evento|Descrição|  
|-----------|-----------------|  
|`RowUpdating`|Uma operação UPDATE, INSERT ou DELETE em uma linha (por uma chamada para uma da `Update` métodos) está prestes a começar.|  
|`RowUpdated`|Uma operação UPDATE, INSERT ou DELETE em uma linha (por uma chamada para uma da `Update` métodos) é concluída.|  
|`FillError`|Ocorreu um erro durante uma `Fill` operação.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating e RowUpdated  
 `RowUpdating`é gerado antes de qualquer atualização para uma linha de <xref:System.Data.DataSet> foi processada na fonte de dados. `RowUpdated`é gerado depois que qualquer atualização para uma linha de `DataSet` foi processada na fonte de dados. Como resultado, você pode usar `RowUpdating` para modificar o comportamento da atualização antes que elas ocorram, para fornecer manipulação adicional quando uma atualização ocorrerá, para manter uma referência a uma linha atualizada, para cancelar a atualização atual e a agenda para um lote de processar a ser processada mais tarde , e assim por diante. `RowUpdated`é útil para responder a erros e exceções que ocorrem durante a atualização. Você pode adicionar informações de erro para o `DataSet`, bem como a lógica de repetição e assim por diante.  
  
 O <xref:System.Data.Common.RowUpdatingEventArgs> e <xref:System.Data.Common.RowUpdatedEventArgs> argumentos passados para o `RowUpdating` e `RowUpdated` eventos incluem o seguinte: uma `Command` propriedade que faz referência a `Command` do objeto que está sendo usado para executar a atualização; um `Row` propriedade que faz referência a `DataRow` objeto que contém as informações atualizadas; um `StatementType` propriedade para o tipo de atualização está sendo executada; o `TableMapping`, se aplicável; e o `Status` da operação.  
  
 Você pode usar o `Status` para determinar se ocorreu um erro durante a operação e, se desejado, para controlar as ações em relação as linhas atuais e resultantes. Quando o evento ocorre, o `Status` propriedade é igual a `Continue` ou `ErrorsOccurred`. A tabela a seguir mostra os valores para o qual você pode definir o `Status` propriedade para controlar as ações posteriores durante a atualização.  
  
|Status|Descrição|  
|------------|-----------------|  
|`Continue`|Continue a operação de atualização.|  
|`ErrorsOccurred`|Anular a operação de atualização e gerará uma exceção.|  
|`SkipCurrentRow`|Ignorar a linha atual e continuar a operação de atualização.|  
|`SkipAllRemainingRows`|Anular a operação de atualização, mas não lançar uma exceção.|  
  
 Definindo o `Status` propriedade `ErrorsOccurred` faz com que uma exceção seja lançada. Você pode controlar quais exceção definindo o `Errors` propriedade para a exceção desejada. Usando um dos outros valores para `Status` impede uma exceção de que está sendo gerada.  
  
 Você também pode usar o `ContinueUpdateOnError` linhas atualizadas de propriedade para lidar com erros. Se `DataAdapter.ContinueUpdateOnError` é `true`, quando uma atualização para os resultados de uma linha em uma exceção sendo lançada, o texto da exceção é colocado no `RowError` informações de linha específica e o processamento continuará sem gerar uma exceção. Isso permite que você responda a erros quando o `Update` estiver concluída, em comparação com o `RowUpdated` evento, que permite que você responda a erros quando o erro for encontrado.  
  
 O exemplo de código a seguir mostra como adicionar e remover manipuladores de eventos. O `RowUpdating` manipulador de eventos grava um log de todos os registros excluídos com um carimbo de hora. O `RowUpdated` manipulador de eventos adiciona informações de erro para o `RowError` propriedade da linha a `DataSet`, suprime a exceção e continua o processamento (espelhamento o comportamento de `ContinueUpdateOnError`  =  `true`).  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,   
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a>FillError  
 O `DataAdapter` problemas de `FillError` evento quando ocorre um erro durante uma `Fill` operação. Esse tipo de erro normalmente ocorre quando os dados na linha que está sendo adicionado não podem ser convertidos em um tipo do .NET Framework sem perda de precisão.  
  
 Se ocorrer um erro durante uma `Fill` operação, a linha atual não é adicionada para o `DataTable`. O `FillError` evento permite que você para resolver o erro e adicione a linha, ou ignorar a linha excluída e continuar o `Fill` operação.  
  
 O `FillErrorEventArgs` passado para o `FillError` eventos podem conter várias propriedades que permitem que você deve responder e resolver erros. A tabela a seguir mostra as propriedades do `FillErrorEventArgs` objeto.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|`Errors`|O `Exception` que ocorreu.|  
|`DataTable`|O `DataTable` do objeto que está sendo preenchido quando o erro ocorreu.|  
|`Values`|Uma matriz de objetos que contém os valores da linha que está sendo adicionado quando o erro ocorreu. O ordinal de referências da `Values` matriz correspondem às referências ordinais das colunas da linha que está sendo adicionado. Por exemplo, `Values[0]` é o valor que estava sendo adicionado como a primeira coluna da linha.|  
|`Continue`|Permite que você escolha se deseja ou não lançar uma exceção. Definindo o `Continue` propriedade `false` interromperá atual `Fill` operação e uma exceção serão lançada. Configuração `Continue` para `true` continua a `Fill` operação apesar do erro.|  
  
 O exemplo de código a seguir adiciona um manipulador de eventos para o `FillError` evento o `DataAdapter`. No `FillError` código de evento, o exemplo determina se há a possibilidade de perda de precisão, fornecendo a oportunidade de responder à exceção.  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    args.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    args.RowError =   
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Handling DataSet Events](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md) (Manipulando eventos do DataSet)  
 [Manipulação de eventos de DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [Eventos](../../../../docs/standard/events/index.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
