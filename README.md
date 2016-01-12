# payfirma-ecommerce-c-sharp


Usage Example:

```
com.payfirma.ecommerce.PayfirmaTransaction payfirma =
    new com.payfirma.ecommerce.PayfirmaTransaction();

// Credentials
com.payfirma.ecommerce.PayfirmaCredentials credentials = new
    com.payfirma.ecommerce.PayfirmaCredentials();
credentials.APIKey = "YOUR API KEY";
credentials.MerchantID = "YOU MERCHANT ID";

// Credit Card Info
com.payfirma.ecommerce.PayfirmaCreditCard cc =
    new com.payfirma.ecommerce.PayfirmaCreditCard();
cc.Number = "4111111111111111";
cc.ExpMonth = 11;
cc.ExpYear = 2018;
cc.CVV2 = "123";

// Extra Meta Data
com.payfirma.ecommerce.PayfirmaMetaData payfirmaMeta =
    new com.payfirma.ecommerce.PayfirmaMetaData();
payfirmaMeta.Firstname = "Firstname";
payfirmaMeta.Lastname = "Lastname";
payfirmaMeta.AmountTax = "1.11";
payfirmaMeta.Email = "bentolila@github.com";


// Sale Request
com.payfirma.ecommerce.PayfirmaTransactionResponse saleResponse =
    payfirma.ProcessSale(credentials, cc, payfirmaMeta, 21.11, true);

Console.WriteLine("//// SALE /////");
Console.WriteLine(saleResponse.ToString());
Console.WriteLine(Environment.NewLine);

// Refund Request
com.payfirma.ecommerce.PayfirmaTransactionResponse refundResponse =
    payfirma.ProcessRefund(credentials, saleResponse.TransactionId, 10.11, true);

Console.WriteLine("//// REFUND /////");
Console.WriteLine(refundResponse.ToString());
Console.WriteLine(Environment.NewLine);

// Authorization Request
com.payfirma.ecommerce.PayfirmaTransactionResponse authResponse =
    payfirma.ProcessAuthorize(credentials, cc, payfirmaMeta, 21.11, true);

Console.WriteLine("//// AUTHORIZATION /////");
Console.WriteLine(authResponse.ToString());
Console.WriteLine(Environment.NewLine);

// Capture Request
com.payfirma.ecommerce.PayfirmaTransactionResponse captureResponse =
    payfirma.ProcessCapture(credentials, authResponse.TransactionId, 21.11, true);

Console.WriteLine("//// CAPTURE /////");
Console.WriteLine(captureResponse.ToString());
Console.WriteLine(Environment.NewLine);

```

Note: When testing transactions, any amount that is a whole, odd dollar amount will result in an Approved transaction: $51.20, $229.83. Any amount that is a whole, even dollar amount will result in a Declined transactions: $40.11, $102.34. Whatever amount following the decimal point (cents) do not affect test transactions.
