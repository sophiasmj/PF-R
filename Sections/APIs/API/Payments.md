Payments
============

The Payment API is used for processing, and viewing payment information on the PayFabric Receivables website. Please note that all requests require API authentication, see our [guide](Token.md) on how to authenticate.


Process a Payment
--------------------

* `POST /payments/process` will process a payment on the PayFabric Receivables website based on the JSON request payload.

###### Request
<pre>
{
	<b>"CustomerId": "Nodus0001"</b>,
	"Currency": "USD",
	"PaymentApplies": [{
		"AppliedToInvoice": true,
		"InvoiceId": "STDINV2006",
		"Identity": "",	
		"PayAmount": 1.00,
		"DocumentType": 3
	}],
	"ApplyCredit": {
		"CreditApplies": {
			"AppliedToInvoice": true,
			"InvoiceId": "STDINV2006",
			"Identity": "",	
			"PayAmount": 1.00,
			"DocumentType": 3
		},
		"Identity": "",
		"PaymentId": "APIPMT00000001"
	},
	"Prepayment": 1.00,
	"AdditionalFee": 0.00,
	"ScheduleDate": "2018-08-02",
	"Comment": "ABC",
	"WalletEntryGuid": "4bc44ebe-118a-46d1-a526-882a0e5c2aac"
	"PaymentMethod": "CreditCard",
	"SaveWallet": false,
	"CVV2": "123"
}
</pre>

Please note that **bold** fields are required fields, and all others are optional. For more information and descriptions on available fields please see our [object reference](../../Objects/ProcessPayment.md#ProcessPaymentPost).

###### Response
<pre>
{
    "PaymentId": "WEBPMT0000000020",
    "EmailGuid": "00000000-0000-0000-0000-000000000000",
    "EmailAddress": "aaronfit0001@nodus.com",
    "AuthCode": "010101",
    "Amount": 0,
    "CreditCardName": null,
    "CreditCardNumber": null,
    "CreditCardType": null,
    "CreditCardExpDate": "0001-01-01T00:00:00",
    "ECheckType": 0,
    "ECheckAccountNumber": null,
    "ECheckAbaNumber": null,
    "ECheckCheckNumber": null,
    "Address1": null,
    "Address2": null,
    "City": null,
    "State": null,
    "Zip": null,
    "Country": null
}
</pre>

For more information and descriptions on available fields please see our [object reference](../Objects/ProcessPayment.md#ProcessPaymentResponse).


Retrieve Payment Receipt
--------------------

* `GET /payments/receipt?paymentId={paymentId}` will get the payment information on the PayFabric Receivables website based on the URL parameters.

###### Request
<pre>
	GET /payments/receipt?paymentId=WEBPMT0000000020
</pre>

###### Response
<pre>
{
    "CreditAmount": 0,
    "AdditionalFee": 0,
    "PrepaymentAmount": 0,
    "Currency": {
        "CurrencyGuid": "1620fcac-35e8-e811-87df-534e57000000",
        "CCSetupId": "PayFlowProCredit",
        "ECSetupId": "PaymentechECheck",
        "IsUsingECheck": true,
        "IsUsingCreditCard": true,
        "IsValid": true,
        "Name": "USD",
        "CurrencyCode": "Z-US$",
        "Symbol": "$",
        "LongName": "US Dollars",
        "IsFuncCurrency": true
    },
    "PaymentStatus": "Processed",
    "Company": {
        "Name": "Nodus Tech",
        "LogoLarge": "",
        "Logo": "data:image/gif;base64,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",
        "Country": "Nodus Tech",
        "Address": "West First Street",
        "Address2": "-",
        "City": "Claremont",
        "State": "CA",
        "Zip": "Claremont, CA 91711",
        "Phone": "909 248 6547",
        "PortalName": "nodus",
        "PortalUrl": "https://sandbox.payfabric.com/receivables/nodus",
        "IntegrationKey": null,
        "IntegrationPassword": null
    },
    "Customer": {
        "Status": "Active",
        "BillingAddress": {
            "Address1": "98765 Crossway Park Dr",
            "Address2": "",
            "Address3": "",
            "City": "Bloomington",
            "Country": "USA",
            "Email": "",
            "Fax": "",
            "Name": "Dennis Swenson",
            "Phone": "",
            "State": "MN",
            "Zip": "55304-9840"
        },
        "PrimaryAddress": {
            "Address1": "98765 Crossway Park Dr",
            "Address2": "",
            "Address3": "",
            "City": "Bloomington",
            "Country": "USA",
            "Email": "",
            "Fax": "",
            "Name": "Dennis Swenson",
            "Phone": "",
            "State": "MN",
            "Zip": "55304-9840"
        },
        "ShippingAddress": {
            "Address1": "98765 Crossway Park Dr",
            "Address2": "",
            "Address3": "",
            "City": "Bloomington",
            "Country": "USA",
            "Email": "",
            "Fax": "",
            "Name": "Dennis Swenson",
            "Phone": "",
            "State": "MN",
            "Zip": "55304-9840"
        },
        "CreditBalance": 0,
        "InvoiceBalance": 0,
        "PastDueBalance": 0,
        "Class": "USA-ILMO-T1",
        "CustomerId": "Nodus0001",
        "CopyEmail": null,
        "Email": "nodus0001@nodus.com",
        "ExtensionData": "",
        "Name": "Nodus Technologies",
        "ParentCustomerId": "",
        "PaymentTerms": "2% 10/Net 30",
        "StatementName": "Nodus Technologies",
        "Currency": "System.Data.Entity.DynamicProxies.Currency_30F089ECC07A0C4D8ED6F4DCCECCB9F0BB430A3CFCDA4043EF8D27F0A890BC94",
        "ShippingMethod": ""
    },
    "Transaction": null,
    "Amount": 200,
    "BalanceAmount": 12.56,
    "BatchNumber": "1234",
    "PaymentMethod": "Cash",
    "CCNumber": "",
    "CheckNumber": "",
    "CreatedOn": "2019-05-21T00:00:00",
    "CustomerId": "Nodus0001",
    "Identity": "PYMNT00000000001",
    "PaymentApplies": [
        {
            "AppliedToInvoice": true,
            "InvoiceId": "ORDST1026",
            "Identity": null,
            "PayAmount": 187.44,
            "DocumentType": 1,
            "RowVersion": "AAAAAAAAB/k="
        }
    ],
    "IsVoid": false,
    "PaymentId": "PYMNT00000000001",
    "PaymentType": "Payment",
    "Notes": ""
}
</pre>

For more information and descriptions on available fields please see our [object reference](../../Objects/PaymentReceipt.md).
