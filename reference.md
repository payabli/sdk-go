# Reference
## Bill
<details><summary><code>client.Bill.AddBill(Entry, request) -> *payabli.BillResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a bill in an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddBillRequest{
        Body: &payabli.BillOutData{
            BillNumber: payabli.String(
                "ABC-123",
            ),
            NetAmount: payabli.Float64(
                3762.87,
            ),
            BillDate: payabli.Time(
                payabli.MustParseDate(
                    "2024-07-01",
                ),
            ),
            DueDate: payabli.Time(
                payabli.MustParseDate(
                    "2024-07-01",
                ),
            ),
            Comments: payabli.String(
                "Deposit for materials",
            ),
            BillItems: []*payabli.BillItem{
                &payabli.BillItem{
                    ItemProductCode: payabli.String(
                        "M-DEPOSIT",
                    ),
                    ItemProductName: payabli.String(
                        "Materials deposit",
                    ),
                    ItemDescription: payabli.String(
                        "Deposit for materials",
                    ),
                    ItemCommodityCode: payabli.String(
                        "010",
                    ),
                    ItemUnitOfMeasure: payabli.String(
                        "SqFt",
                    ),
                    ItemCost: 5,
                    ItemQty: payabli.Int(
                        1,
                    ),
                    ItemMode: payabli.Int(
                        0,
                    ),
                    ItemCategories: []*string{
                        payabli.String(
                            "deposits",
                        ),
                    },
                    ItemTotalAmount: payabli.Float64(
                        123,
                    ),
                    ItemTaxAmount: payabli.Float64(
                        7,
                    ),
                    ItemTaxRate: payabli.Float64(
                        0.075,
                    ),
                },
            },
            Mode: payabli.Int(
                0,
            ),
            AccountingField1: payabli.String(
                "MyInternalId",
            ),
            Vendor: &payabli.VendorData{
                VendorNumber: payabli.String(
                    "1234-A",
                ),
            },
            EndDate: payabli.Time(
                payabli.MustParseDate(
                    "2024-07-01",
                ),
            ),
            Frequency: payabli.FrequencyMonthly.Ptr(),
            Terms: payabli.String(
                "NET30",
            ),
            Status: payabli.Int(
                -99,
            ),
            Attachments: []*payabli.FileContent{
                &payabli.FileContent{
                    Ftype: payabli.FileContentFtypePdf.Ptr(),
                    Filename: payabli.String(
                        "my-doc.pdf",
                    ),
                    Furl: payabli.String(
                        "https://mysite.com/my-doc.pdf",
                    ),
                },
            },
        },
    }
client.Bill.AddBill(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.BillOutData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.DeleteAttachedFromBill(IdBill, Filename) -> *payabli.BillResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a file attached to a bill.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.DeleteAttachedFromBillRequest{}
client.Bill.DeleteAttachedFromBill(
        context.TODO(),
        "0_Bill.pdf",
        285,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idBill:** `int` — Payabli ID for the bill. Get this ID by querying `/api/Query/bills/` for the entrypoint or the organization.
    
</dd>
</dl>

<dl>
<dd>

**filename:** `string` 

The filename in Payabli. Filename is `zipName` in response to a
request to `/api/Invoice/{idInvoice}`. Here, the filename is
`0_Bill.pdf`. 

```json
  "DocumentsRef": {
    "zipfile": "inva_269.zip",
    "filelist": [
      {
        "originalName": "Bill.pdf",
        "zipName": "0_Bill.pdf",
        "descriptor": null
      }
    ]
  }
  ```
    
</dd>
</dl>

<dl>
<dd>

**returnObject:** `*bool` — When `true`, the request returns the file content as a Base64-encoded string.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.DeleteBill(IdBill) -> *payabli.BillResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a bill by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Bill.DeleteBill(
        context.TODO(),
        285,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idBill:** `int` — Payabli ID for the bill. Get this ID by querying `/api/Query/bills/` for the entrypoint or the organization.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.EditBill(IdBill, request) -> *payabli.EditBillResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates a bill by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.BillOutData{
        NetAmount: payabli.Float64(
            3762.87,
        ),
        BillDate: payabli.Time(
            payabli.MustParseDate(
                "2025-07-01",
            ),
        ),
    }
client.Bill.EditBill(
        context.TODO(),
        285,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idBill:** `int` — Payabli ID for the bill. Get this ID by querying `/api/Query/bills/` for the entrypoint or the organization.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.BillOutData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.GetAttachedFromBill(IdBill, Filename) -> *payabli.FileContent</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a file attached to a bill, either as a binary file or as a Base64-encoded string.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.GetAttachedFromBillRequest{
        ReturnObject: payabli.Bool(
            true,
        ),
    }
client.Bill.GetAttachedFromBill(
        context.TODO(),
        "0_Bill.pdf",
        285,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idBill:** `int` — Payabli ID for the bill. Get this ID by querying `/api/Query/bills/` for the entrypoint or the organization.
    
</dd>
</dl>

<dl>
<dd>

**filename:** `string` 

The filename in Payabli. Filename is `zipName` in response to a request to `/api/Invoice/{idInvoice}`. Here, the filename is `0_Bill.pdf``. 
"DocumentsRef": {
  "zipfile": "inva_269.zip",
  "filelist": [
    {
      "originalName": "Bill.pdf",
      "zipName": "0_Bill.pdf",
      "descriptor": null
    }
  ]
}
    
</dd>
</dl>

<dl>
<dd>

**returnObject:** `*bool` — When `true`, the request returns the file content as a Base64-encoded string.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.GetBill(IdBill) -> *payabli.GetBillResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a bill by ID from an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Bill.GetBill(
        context.TODO(),
        285,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idBill:** `int` — Payabli ID for the bill. Get this ID by querying `/api/Query/bills/` for the entrypoint or the organization.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.ListBills(Entry) -> *payabli.BillQueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of bills for an entrypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBillsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Bill.ListBills(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set. 
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response isn't filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `frequency` (`in`, `nin`, `ne`, `eq`)
- `method` (`in`, `nin`, `eq`, `ne`)
- `event` (`in`, `nin`, `eq`, `ne`)
- `target` (`ct`, `nct`, `eq`, `ne`)
- `status` (`eq`, `ne`)
- `approvalUserId` (`eq`, `ne`)
- `parentOrgId` (`ne`, `eq`, `nin`, `in`)
- `approvalUserEmail` (`eq`, `ne`)
- `scheduleId` (`ne`, `eq`)

List of comparison accepted - enclosed between parentheses:
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array
- `nin` => not inside array

List of parameters accepted:
- `limitRecord` : max number of records for query (default="20", "0" or negative value for all)
- `fromRecord` : initial record in query
Example: `totalAmount(gt)=20` returns all records with a `totalAmount` that's greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.ListBillsOrg(OrgId) -> *payabli.BillQueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of bills for an organization. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBillsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Bill.ListBillsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response isn't filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `frequency` (in, nin, ne, eq)
- `method` (in, nin, eq, ne)
- `event` (in, nin, eq, ne)
- `target` (ct, nct, eq, ne)
- `status` (eq, ne)
- `parentOrgId` (ne, eq, nin, in)
- `approvalUserId` (eq, ne)
- `approvalUserEmail` (eq, ne)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: totalAmount(gt)=20 return all records with totalAmount greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.ModifyApprovalBill(IdBill, request) -> *payabli.ModifyApprovalBillResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Modify the list of users the bill is sent to for approval.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := []string{
        "string",
    }
client.Bill.ModifyApprovalBill(
        context.TODO(),
        285,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idBill:** `int` — Payabli ID for the bill. Get this ID by querying `/api/Query/bills/` for the entrypoint or the organization.
    
</dd>
</dl>

<dl>
<dd>

**request:** `[]string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.SendToApprovalBill(IdBill, request) -> *payabli.BillResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Send a bill to a user or list of users to approve.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.SendToApprovalBillRequest{
        IdempotencyKey: payabli.String(
            "6B29FC40-CA47-1067-B31D-00DD010662DA",
        ),
        Body: []string{
            "string",
        },
    }
client.Bill.SendToApprovalBill(
        context.TODO(),
        285,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idBill:** `int` — Payabli ID for the bill. Get this ID by querying `/api/Query/bills/` for the entrypoint or the organization.
    
</dd>
</dl>

<dl>
<dd>

**autocreateUser:** `*bool` — Automatically create the target user for approval if they don't exist.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `[]string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Bill.SetApprovedBill(IdBill, Approved) -> *payabli.SetApprovedBillResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Approve or disapprove a bill by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.SetApprovedBillRequest{}
client.Bill.SetApprovedBill(
        context.TODO(),
        "true",
        285,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idBill:** `int` — Payabli ID for the bill. Get this ID by querying `/api/Query/bills/` for the entrypoint or the organization.
    
</dd>
</dl>

<dl>
<dd>

**approved:** `string` — String representing the approved status. Accepted values: 'true' or 'false'.
    
</dd>
</dl>

<dl>
<dd>

**email:** `*string` — Email or username of user modifying approval status.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Boarding
<details><summary><code>client.Boarding.AddApplication(request) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a boarding application in an organization. This endpoint requires an application API token.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddApplicationRequest{
        ApplicationDataPayIn: &payabli.ApplicationDataPayIn{
            Services: &payabli.ApplicationDataPayInServices{
                Ach: &payabli.ApplicationDataPayInServicesAch{},
                Card: &payabli.ApplicationDataPayInServicesCard{
                    AcceptAmex: payabli.Bool(
                        true,
                    ),
                    AcceptDiscover: payabli.Bool(
                        true,
                    ),
                    AcceptMastercard: payabli.Bool(
                        true,
                    ),
                    AcceptVisa: payabli.Bool(
                        true,
                    ),
                },
            },
            AnnualRevenue: payabli.Float64(
                1000,
            ),
            AverageBillSize: payabli.String(
                "500",
            ),
            AverageMonthlyBill: payabli.String(
                "5650",
            ),
            Avgmonthly: payabli.Float64(
                1000,
            ),
            Baddress: payabli.String(
                "123 Walnut Street",
            ),
            Baddress1: payabli.String(
                "Suite 103",
            ),
            BankData: &payabli.ApplicationDataPayInBankData{},
            Bcity: payabli.String(
                "New Vegas",
            ),
            Bcountry: payabli.String(
                "US",
            ),
            Binperson: payabli.Int(
                60,
            ),
            Binphone: payabli.Int(
                20,
            ),
            Binweb: payabli.Int(
                20,
            ),
            Bstate: payabli.String(
                "FL",
            ),
            Bsummary: payabli.String(
                "Brick and mortar store that sells office supplies",
            ),
            Btype: payabli.OwnTypeLimitedLiabilityCompany.Ptr(),
            Bzip: payabli.String(
                "33000",
            ),
            Contacts: []*payabli.ApplicationDataPayInContactsItem{
                &payabli.ApplicationDataPayInContactsItem{
                    ContactEmail: payabli.String(
                        "herman@hermanscoatings.com",
                    ),
                    ContactName: payabli.String(
                        "Herman Martinez",
                    ),
                    ContactPhone: payabli.String(
                        "3055550000",
                    ),
                    ContactTitle: payabli.String(
                        "Owner",
                    ),
                },
            },
            CreditLimit: payabli.String(
                "creditLimit",
            ),
            DbaName: payabli.String(
                "Sunshine Gutters",
            ),
            Ein: payabli.String(
                "123456789",
            ),
            Faxnumber: payabli.String(
                "1234567890",
            ),
            Highticketamt: payabli.Float64(
                1000,
            ),
            LegalName: payabli.String(
                "Sunshine Services, LLC",
            ),
            License: payabli.String(
                "2222222FFG",
            ),
            Licstate: payabli.String(
                "CA",
            ),
            Maddress: payabli.String(
                "123 Walnut Street",
            ),
            Maddress1: payabli.String(
                "STE 900",
            ),
            Mcc: payabli.String(
                "7777",
            ),
            Mcity: payabli.String(
                "Johnson City",
            ),
            Mcountry: payabli.String(
                "US",
            ),
            Mstate: payabli.String(
                "TN",
            ),
            Mzip: payabli.String(
                "37615",
            ),
            OrgId: payabli.Int64(
                123,
            ),
            Ownership: []*payabli.ApplicationDataPayInOwnershipItem{
                &payabli.ApplicationDataPayInOwnershipItem{
                    Oaddress: payabli.String(
                        "33 North St",
                    ),
                    Ocity: payabli.String(
                        "Any City",
                    ),
                    Ocountry: payabli.String(
                        "US",
                    ),
                    Odriverstate: payabli.String(
                        "CA",
                    ),
                    Ostate: payabli.String(
                        "CA",
                    ),
                    Ownerdob: payabli.String(
                        "01/01/1990",
                    ),
                    Ownerdriver: payabli.String(
                        "CA6677778",
                    ),
                    Owneremail: payabli.String(
                        "test@email.com",
                    ),
                    Ownername: payabli.String(
                        "John Smith",
                    ),
                    Ownerpercent: payabli.Int(
                        100,
                    ),
                    Ownerphone1: payabli.String(
                        "555888111",
                    ),
                    Ownerphone2: payabli.String(
                        "555888111",
                    ),
                    Ownerssn: payabli.String(
                        "123456789",
                    ),
                    Ownertitle: payabli.String(
                        "CEO",
                    ),
                    Ozip: payabli.String(
                        "55555",
                    ),
                },
            },
            Phonenumber: "1234567890",
            ProcessingRegion: "US",
            RecipientEmail: payabli.String(
                "josephray@example.com",
            ),
            RecipientEmailNotification: payabli.Bool(
                true,
            ),
            Resumable: payabli.Bool(
                true,
            ),
            Signer: &payabli.SignerDataRequest{
                Address: payabli.String(
                    "33 North St",
                ),
                Address1: payabli.String(
                    "STE 900",
                ),
                City: payabli.String(
                    "Bristol",
                ),
                Country: payabli.String(
                    "US",
                ),
                Dob: payabli.String(
                    "01/01/1976",
                ),
                Email: payabli.String(
                    "test@email.com",
                ),
                Name: payabli.String(
                    "John Smith",
                ),
                Phone: payabli.String(
                    "555888111",
                ),
                Ssn: payabli.String(
                    "123456789",
                ),
                State: payabli.String(
                    "TN",
                ),
                Zip: payabli.String(
                    "55555",
                ),
                PciAttestation: payabli.Bool(
                    true,
                ),
                SignedDocumentReference: payabli.String(
                    "https://example.com/signed-document.pdf",
                ),
                AttestationDate: payabli.String(
                    "04/20/2025",
                ),
                SignDate: payabli.String(
                    "04/20/2025",
                ),
                AdditionalData: payabli.String(
                    `{"deviceId":"499585-389fj484-3jcj8hj3","session":"fifji4-fiu443-fn4843","timeWithCompany":"6 Years"}`,
                ),
            },
            Startdate: payabli.String(
                "01/01/1990",
            ),
            TaxFillName: payabli.String(
                "Sunshine LLC",
            ),
            TemplateId: payabli.Int64(
                22,
            ),
            Ticketamt: payabli.Float64(
                1000,
            ),
            Website: payabli.String(
                "www.example.com",
            ),
            WhenCharged: payabli.WhenchargedWhenServiceProvided,
            WhenDelivered: payabli.WhendeliveredOver30Days,
            WhenProvided: payabli.WhenprovidedThirtyDaysOrLess,
            WhenRefunded: payabli.WhenrefundedThirtyDaysOrLess,
        },
    }
client.Boarding.AddApplication(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*payabli.AddApplicationRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.DeleteApplication(AppId) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a boarding application by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Boarding.DeleteApplication(
        context.TODO(),
        352,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**appId:** `int` — Boarding application ID. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.GetApplication(AppId) -> *payabli.ApplicationDetailsRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves the details for a boarding application by ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Boarding.GetApplication(
        context.TODO(),
        352,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**appId:** `int` — Boarding application ID.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.GetApplicationByAuth(XId, request) -> *payabli.ApplicationQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Gets a boarding application by authentication information. This endpoint requires an `application` API token. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RequestAppByAuth{
        Email: payabli.String(
            "admin@email.com",
        ),
        ReferenceId: payabli.String(
            "n6UCd1f1ygG7",
        ),
    }
client.Boarding.GetApplicationByAuth(
        context.TODO(),
        "17E",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**xId:** `string` — The application ID in Hex format. Find this at the end of the boarding link URL returned in a call to api/Boarding/applink/{appId}/{mail2}. For example in:  `https://boarding-sandbox.payabli.com/boarding/externalapp/load/17E`, the xId is `17E`. 
    
</dd>
</dl>

<dl>
<dd>

**email:** `*payabli.Email` — The email address the applicant used to save the application.
    
</dd>
</dl>

<dl>
<dd>

**referenceId:** `*string` — The referenceId is sent to the applicant via email when they save the application.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.GetByIdLinkApplication(BoardingLinkId) -> *payabli.BoardingLinkQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves details for a boarding link, by ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Boarding.GetByIdLinkApplication(
        context.TODO(),
        91,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**boardingLinkId:** `int` — The boarding link ID. You can find this at the end of the boarding link reference name. For example `https://boarding.payabli.com/boarding/app/myorgaccountname-00091`. The ID is `91`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.GetByTemplateIdLinkApplication(TemplateId) -> *payabli.BoardingLinkQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get details for a boarding link using the boarding template ID. This endpoint requires an application API token.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Boarding.GetByTemplateIdLinkApplication(
        context.TODO(),
        80,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**templateId:** `float64` — The boarding template ID. You can find this at the end of the boarding template URL in PartnerHub. Example: `https://partner-sandbox.payabli.com/myorganization/boarding/edittemplate/80`. Here, the template ID is `80`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.GetExternalApplication(AppId, Mail2) -> *payabli.PayabliApiResponse00</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a link and the verification code used to log into an existing boarding application. You can also use this endpoint to send a link and referenceId for an existing boarding application to an email address. The recipient can use the referenceId and email address to access and edit the application.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.GetExternalApplicationRequest{}
client.Boarding.GetExternalApplication(
        context.TODO(),
        352,
        "mail2",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**appId:** `int` — Boarding application ID. 
    
</dd>
</dl>

<dl>
<dd>

**mail2:** `string` — Email address used to access the application. If `sendEmail` parameter is true, a link to the application is sent to this email address.
    
</dd>
</dl>

<dl>
<dd>

**sendEmail:** `*bool` — If `true`, sends an email that includes the link to the application to the `mail2` address. Defaults to `false`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.GetLinkApplication(BoardingLinkReference) -> *payabli.BoardingLinkQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves the details for a boarding link, by reference name. This endpoint requires an application API token.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Boarding.GetLinkApplication(
        context.TODO(),
        "myorgaccountname-00091",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**boardingLinkReference:** `string` — The boarding link reference name. You can find this at the end of the boarding link URL. For example `https://boarding.payabli.com/boarding/app/myorgaccountname-00091`
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.ListApplications(OrgId) -> *payabli.QueryBoardingAppsListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of boarding applications for an organization. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListApplicationsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Boarding.ListApplications(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `createdAt` (gt, ge, lt, le, eq, ne)
- `startDate` (gt, ge, lt, le, eq, ne)
- `dbaname` (ct, nct)
- `legalname` (ct, nct)
- `ein` (ct, nct)
- `address` (ct, nct)
- `city` (ct, nct)
- `state` (ct, nct)
- `phone` (ct, nct)
- `mcc` (ct, nct)
- `owntype` (ct, nct)
- `ownerName` (ct, nct)
- `contactName` (ct, nct)
- `status` (in, nin, eq,ne)
- `orgParentname` (ct, nct)
- `externalpaypointID` (ct, nct, eq, ne)
- `repCode` (ct, nct, eq, ne)
- `repName` (ct, nct, eq, ne)
- `repOffice` (ct, nct, eq, ne)
List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.ListBoardingLinks(OrgId) -> *payabli.QueryBoardingLinksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Return a list of boarding links for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBoardingLinksRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Boarding.ListBoardingLinks(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `lastUpdated` (gt, ge, lt, le, eq, ne)
- `templateName` (ct, nct)
- `referenceName` (ct, nct)
- `acceptRegister` (eq, ne)
- `acceptAuth` (eq, ne)
- `templateCode` (ct, nct)
- `templateId` (eq, ne)
- `orgParentname` (ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than 
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: templateName(ct)=hoa return all records with template title containing "hoa"
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Boarding.UpdateApplication(AppId, request) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates a boarding application by ID. This endpoint requires an application API token.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ApplicationData{}
client.Boarding.UpdateApplication(
        context.TODO(),
        352,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**appId:** `int` — Boarding application ID. 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.ApplicationData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## ChargeBacks
<details><summary><code>client.ChargeBacks.AddResponse(Id, request) -> *payabli.AddResponseResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Add a response to a chargeback or ACH return.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ResponseChargeBack{
        IdempotencyKey: payabli.String(
            "6B29FC40-CA47-1067-B31D-00DD010662DA",
        ),
    }
client.ChargeBacks.AddResponse(
        context.TODO(),
        1000000,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `int64` — ID of the chargeback or return record.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**attachments:** `*payabli.Attachments` — Array of attached files to response.
    
</dd>
</dl>

<dl>
<dd>

**contactEmail:** `*payabli.Email` — Email of response submitter.
    
</dd>
</dl>

<dl>
<dd>

**contactName:** `*string` — Name of response submitter
    
</dd>
</dl>

<dl>
<dd>

**notes:** `*string` — Response notes
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.ChargeBacks.GetChargeback(Id) -> *payabli.ChargebackQueryRecords</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a chargeback record and its details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.ChargeBacks.GetChargeback(
        context.TODO(),
        1000000,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `int64` — ID of the chargeback or return record. This is returned as `chargebackId` in the [RecievedChargeback](/developers/developer-guides/webhook-payloads#receivedChargeback) and [ReceivedAchReturn](/developers/developer-guides/webhook-payloads#receivedachreturn) webhook notifications.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.ChargeBacks.GetChargebackAttachment(Id, FileName) -> string</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a chargeback attachment file by its file name.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.ChargeBacks.GetChargebackAttachment(
        context.TODO(),
        1000000,
        "fileName",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `int64` — The ID of chargeback or return record.
    
</dd>
</dl>

<dl>
<dd>

**fileName:** `string` — The chargeback attachment's file name.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## CheckCapture
<details><summary><code>client.CheckCapture.CheckProcessing(request) -> *payabli.CheckCaptureResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Captures a check for Remote Deposit Capture (RDC) using the provided check images and details. This endpoint handles the OCR extraction of check data including MICR, routing number, account number, and amount. See the [RDC guide](/developers/developer-guides/pay-in-rdc) for more details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.CheckCaptureRequestBody{
        EntryPoint: "47abcfea12",
        FrontImage: "/9j/4AAQSkZJRgABAQEASABIAAD...",
        RearImage: "/9j/4AAQSkZJRgABAQEASABIAAD...",
        CheckAmount: 12550,
    }
client.CheckCapture.CheckProcessing(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entryPoint:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**frontImage:** `string` — Base64-encoded front check image. Must be JPEG or PNG format and less than 1MB. Image must show the entire check clearly with no partial, blurry, or illegible portions.
    
</dd>
</dl>

<dl>
<dd>

**rearImage:** `string` — Base64-encoded rear check image. Must be JPEG or PNG format and less than 1MB. Image must show the entire check clearly with no partial, blurry, or illegible portions.
    
</dd>
</dl>

<dl>
<dd>

**checkAmount:** `int` — Check amount in cents (maximum 32-bit integer value).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Cloud
<details><summary><code>client.Cloud.AddDevice(Entry, request) -> *payabli.AddDeviceResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Register a cloud device to an entrypoint. See [Devices Quickstart](/developers/developer-guides/devices-quickstart#devices-quickstart) for a complete guide.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.DeviceEntry{
        RegistrationCode: payabli.String(
            "YS7DS5",
        ),
        Description: payabli.String(
            "Front Desk POS",
        ),
    }
client.Cloud.AddDevice(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**description:** `*string` — Description or name for the device. This can be anything, but Payabli recommends entering the name of the paypoint, or some other easy to identify descriptor. If you have several devices for one paypoint, you can give them descriptions like "Cashier 1" and "Cashier 2", or "Front Desk" and "Back Office"
    
</dd>
</dl>

<dl>
<dd>

**registrationCode:** `*string` 

The device registration code or serial number, depending on the model.

- Ingenico devices: This is the activation code that's displayed on the device screen during setup.

- PAX A920 device: This code is the serial number on the back of the device.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Cloud.HistoryDevice(Entry, DeviceId) -> *payabli.CloudQueryApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve the registration history for a device. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Cloud.HistoryDevice(
        context.TODO(),
        "WXGDWB",
        "8cfec329267",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**deviceId:** `string` — ID of the cloud device. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Cloud.ListDevice(Entry) -> *payabli.CloudQueryApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a list of cloud devices registered to an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListDeviceRequest{}
client.Cloud.ListDevice(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**forceRefresh:** `*bool` — When `true`, the request retrieves an updated list of devices from the processor instead of returning a cached list of devices.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Cloud.RemoveDevice(Entry, DeviceId) -> *payabli.RemoveDeviceResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Remove a cloud device from an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Cloud.RemoveDevice(
        context.TODO(),
        "6c361c7d-674c-44cc-b790-382b75d1xxx",
        "8cfec329267",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**deviceId:** `string` — ID of the cloud device. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Customer
<details><summary><code>client.Customer.AddCustomer(Entry, request) -> *payabli.PayabliApiResponseCustomerQuery</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a customer in an entrypoint. An identifier is required to create customer records. Change your identifier settings in Settings > Custom Fields in PartnerHub. 
If you don't include an identifier, the record is rejected.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddCustomerRequest{
        Body: &payabli.CustomerData{
            CustomerNumber: payabli.String(
                "12356ACB",
            ),
            Firstname: payabli.String(
                "Irene",
            ),
            Lastname: payabli.String(
                "Canizales",
            ),
            Address1: payabli.String(
                "123 Bishop's Trail",
            ),
            City: payabli.String(
                "Mountain City",
            ),
            State: payabli.String(
                "TN",
            ),
            Zip: payabli.String(
                "37612",
            ),
            Country: payabli.String(
                "US",
            ),
            Email: payabli.String(
                "irene@canizalesconcrete.com",
            ),
            IdentifierFields: &payabli.Identifierfields{
                payabli.String(
                    "email",
                ),
            },
            TimeZone: payabli.Int(
                -5,
            ),
        },
    }
client.Customer.AddCustomer(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entrypointfield` 
    
</dd>
</dl>

<dl>
<dd>

**forceCustomerCreation:** `*bool` — When `true`, the request creates a new customer record, regardless of whether customer identifiers match an existing customer.
    
</dd>
</dl>

<dl>
<dd>

**replaceExisting:** `*int` — Flag indicating to replace existing customer with a new record. Possible values: 0 (don't replace), 1 (replace). Default is `0`.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.CustomerData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Customer.DeleteCustomer(CustomerId) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a customer record.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Customer.DeleteCustomer(
        context.TODO(),
        998,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**customerId:** `int` — Payabli-generated customer ID. Maps to "Customer ID" column in PartnerHub. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Customer.GetCustomer(CustomerId) -> *payabli.CustomerQueryRecords</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a customer's record and details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Customer.GetCustomer(
        context.TODO(),
        998,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**customerId:** `int` — Payabli-generated customer ID. Maps to "Customer ID" column in PartnerHub. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Customer.LinkCustomerTransaction(CustomerId, TransId) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Links a customer to a transaction by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Customer.LinkCustomerTransaction(
        context.TODO(),
        998,
        "45-as456777hhhhhhhhhh77777777-324",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**customerId:** `int` — Payabli-generated customer ID. Maps to "Customer ID" column in PartnerHub. 
    
</dd>
</dl>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Customer.RequestConsent(CustomerId) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Sends the consent opt-in email to the customer email address in the customer record.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Customer.RequestConsent(
        context.TODO(),
        998,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**customerId:** `int` — Payabli-generated customer ID. Maps to "Customer ID" column in PartnerHub. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Customer.UpdateCustomer(CustomerId, request) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update a customer record. Include only the fields you want to change.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.CustomerData{
        Firstname: payabli.String(
            "Irene",
        ),
        Lastname: payabli.String(
            "Canizales",
        ),
        Address1: payabli.String(
            "145 Bishop's Trail",
        ),
        City: payabli.String(
            "Mountain City",
        ),
        State: payabli.String(
            "TN",
        ),
        Zip: payabli.String(
            "37612",
        ),
        Country: payabli.String(
            "US",
        ),
    }
client.Customer.UpdateCustomer(
        context.TODO(),
        998,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**customerId:** `int` — Payabli-generated customer ID. Maps to "Customer ID" column in PartnerHub. 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.CustomerData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Export
<details><summary><code>client.Export.ExportApplications(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of boarding applications for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportApplicationsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportApplications(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
- `createdAt` (gt, ge, lt, le, eq, ne)
- `startDate` (gt, ge, lt, le, eq, ne)
- `dbaname`  (ct, nct)
- `legalname`  (ct, nct)
- `ein`  (ct, nct)
- `address`  (ct, nct)
- `city`  (ct, nct)
- `state`  (ct, nct)
- `phone`  (ct, nct)
- `mcc`  (ct, nct)
- `owntype`  (ct, nct)
- `ownerName`  (ct, nct)
- `contactName`  (ct, nct)
- `status`  (eq, ne)
- `orgParentname`  (ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- `limitRecord` : max number of records for query (default="20", "0" or negative value for all)
- `fromRecord` : initial record in query

Example: `dbaname(ct)=hoa` returns all records with a `dbaname` containing "hoa"
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportBatchDetails(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

This endpoint is deprecated. Export batch details for a paypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportBatchDetailsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportBatchDetails(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

**List of field names accepted:**

  - `settlementDate` (gt, ge, lt, le, eq, ne)
  - `depositDate` (gt, ge, lt, le, eq, ne)
  - `transId`  (ne, eq, ct, nct)
  - `gatewayTransId`  (ne, eq, ct, nct)
  - `method`   (in, nin, eq, ne)
  - `settledAmount`  (gt, ge, lt, le, eq, ne)
  - `operation`    (in, nin, eq, ne)
  - `source`   (in, nin, eq, ne)
  - `batchNumber`  (ct, nct, eq, ne)
  - `payaccountLastfour`   (nct, ct)
  - `payaccountType`   (ne, eq, in, nin)
  - `customerFirstname`   (ct, nct, eq, ne)
  - `customerLastname`    (ct, nct, eq, ne)
  - `customerName`   (ct, nct)
  - `customerId`  (eq, ne)
  - `customerNumber`  (ct, nct, eq, ne)
  - `customerCompanyname`    (ct, nct, eq, ne)
  - `customerAddress` (ct, nct, eq, ne)
  - `customerCity`    (ct, nct, eq, ne)
  - `customerZip` (ct, nct, eq, ne)
  - `customerState` (ct, nct, eq, ne)
  - `customerCountry` (ct, nct, eq, ne)
  - `customerPhone` (ct, nct, eq, ne)
  - `customerEmail` (ct, nct, eq, ne)
  - `customerShippingAddress` (ct, nct, eq, ne)
  - `customerShippingCity`    (ct, nct, eq, ne)
  - `customerShippingZip` (ct, nct, eq, ne)
  - `customerShippingState` (ct, nct, eq, ne)
  - `customerShippingCountry` (ct, nct, eq, ne)
  - `orgId`  (eq) *mandatory when entry=org*
  - `isHold` (eq, ne)
  - `paypointId`  (ne, eq)
  - `paypointLegal`  (ne, eq, ct, nct)
  - `paypointDba`  (ne, eq, ct, nct)
  - `orgName`  (ne, eq, ct, nct)
  - `batchId` (ct, nct, eq, neq)
  - `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: `amount(gt)=20` return all records with amount greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportBatchDetailsOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

This endpoint is deprecated. Export batch details for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportBatchDetailsOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportBatchDetailsOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

**List of field names accepted:**

  - `settlementDate` (gt, ge, lt, le, eq, ne)
  - `depositDate` (gt, ge, lt, le, eq, ne)
  - `transId`  (ne, eq, ct, nct)
  - `gatewayTransId`  (ne, eq, ct, nct)
  - `method`   (in, nin, eq, ne)
  - `settledAmount`  (gt, ge, lt, le, eq, ne)
  - `operation`    (in, nin, eq, ne)
  - `source`   (in, nin, eq, ne)
  - `batchNumber`  (ct, nct, eq, ne)
  - `payaccountLastfour`   (nct, ct)
  - `payaccountType`   (ne, eq, in, nin)
  - `customerFirstname`   (ct, nct, eq, ne)
  - `customerLastname`    (ct, nct, eq, ne)
  - `customerName`   (ct, nct)
  - `customerId`  (eq, ne)
  - `customerNumber`  (ct, nct, eq, ne)
  - `customerCompanyname`    (ct, nct, eq, ne)
  - `customerAddress` (ct, nct, eq, ne)
  - `customerCity`    (ct, nct, eq, ne)
  - `customerZip` (ct, nct, eq, ne)
  - `customerState` (ct, nct, eq, ne)
  - `customerCountry` (ct, nct, eq, ne)
  - `customerPhone` (ct, nct, eq, ne)
  - `customerEmail` (ct, nct, eq, ne)
  - `customerShippingAddress` (ct, nct, eq, ne)
  - `customerShippingCity`    (ct, nct, eq, ne)
  - `customerShippingZip` (ct, nct, eq, ne)
  - `customerShippingState` (ct, nct, eq, ne)
  - `customerShippingCountry` (ct, nct, eq, ne)
  - `orgId`  (eq) *mandatory when entry=org*
  - `isHold` (eq, ne)
  - `paypointId`  (ne, eq)
  - `paypointLegal`  (ne, eq, ct, nct)
  - `paypointDba`  (ne, eq, ct, nct)
  - `orgName`  (ne, eq, ct, nct)
  - `batchId` (ct, nct, eq, neq)
  - `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: `amount(gt)=20` return all records with amount greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportBatches(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of batches for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportBatchesRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportBatches(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `batchDate` (gt, ge, lt, le, eq, ne)
- `batchNumber` (ne, eq)
- `connectorName` (ne, eq, ct, nct)
- `method` (in, nin, eq, ne)
- `batchAmount` (gt, ge, lt, le, eq, ne)
- `feeBatchAmount` (gt, ge, lt, le, eq, ne)
- `netBatchAmount` (gt, ge, lt, le, eq, ne)
- `releaseAmount` (gt, ge, lt, le, eq, ne)
- `heldAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `paypointId` (ne, eq)
- `externalPaypointID` (ct, nct, eq, ne)
- `expectedDepositDate` (gt, ge, lt, le, eq, ne)
- `batchRecords` (gt, ge, lt, le, eq, ne)
- `transferId` (ne, eq)
- `transferDate` (gt, ge, lt, le, eq, ne)
- `grossAmount` (gt, ge, lt, le, eq, ne)
- `chargeBackAmount` (gt, ge, lt, le, eq, ne)
- `returnedAmount` (gt, ge, lt, le, eq, ne)
- `billingFeeAmount` (gt, ge, lt, le, eq, ne)
- `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)
- `netFundedAmount` (gt, ge, lt, le, eq, ne)
- `adjustmentAmount` (gt, ge, lt, le, eq, ne)
- `processor` (ne, eq, ct, nct)
- `transferStatus` (ne, eq, in, nin)

List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: `batchAmount(gt)=20` returns all records with a `batchAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportBatchesOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of batches for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportBatchesOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportBatchesOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `batchDate` (gt, ge, lt, le, eq, ne)
- `batchNumber` (ne, eq)
- `connectorName` (ne, eq, ct, nct)
- `method` (in, nin, eq, ne)
- `batchAmount` (gt, ge, lt, le, eq, ne)
- `feeBatchAmount` (gt, ge, lt, le, eq, ne)
- `netBatchAmount` (gt, ge, lt, le, eq, ne)
- `releaseAmount` (gt, ge, lt, le, eq, ne)
- `heldAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `paypointId` (ne, eq)
- `externalPaypointID` (ct, nct, eq, ne)
- `expectedDepositDate` (gt, ge, lt, le, eq, ne)
- `batchRecords` (gt, ge, lt, le, eq, ne)
- `transferId` (ne, eq)
- `transferDate` (gt, ge, lt, le, eq, ne)
- `grossAmount` (gt, ge, lt, le, eq, ne)
- `chargeBackAmount` (gt, ge, lt, le, eq, ne)
- `returnedAmount` (gt, ge, lt, le, eq, ne)
- `billingFeeAmount` (gt, ge, lt, le, eq, ne)
- `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)
- `netFundedAmount` (gt, ge, lt, le, eq, ne)
- `adjustmentAmount` (gt, ge, lt, le, eq, ne)
- `processor` (ne, eq, ct, nct)
- `transferStatus` (ne, eq, in, nin)

List of parameters accepted:
- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query
Example: `batchAmount(gt)=20` returns all records with a `batchAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportBatchesOut(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of money out batches for a paypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportBatchesOutRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportBatchesOut(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
  - `batchDate` (gt, ge, lt, le, eq, ne)
  - `batchNumber` (ne, eq)
  - `batchAmount` (gt, ge, lt, le, eq, ne)
  - `status` (in, nin, eq, ne)
  - `paypointLegal` (ne, eq, ct, nct)
  - `paypointDba` (ne, eq, ct, nct)
  - `orgName` (ne, eq, ct, nct, nin, in)
  - `paypointId` (ne, eq)
  - `externalPaypointID` (ct, nct, eq, ne)
List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: `batchAmount(gt)=20` returns all records with a `batchAmount` greater than 20.00"
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportBatchesOutOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of money out batches for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportBatchesOutOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportBatchesOutOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
  - `batchDate` (gt, ge, lt, le, eq, ne)
  - `batchNumber` (ne, eq)
  - `batchAmount` (gt, ge, lt, le, eq, ne)
  - `status` (in, nin, eq, ne)
  - `paypointLegal` (ne, eq, ct, nct)
  - `paypointDba` (ne, eq, ct, nct)
  - `orgName` (ne, eq, ct, nct, nin, in)
  - `paypointId` (ne, eq)
  - `externalPaypointID` (ct, nct, eq, ne)
List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: `batchAmount(gt)=20` returns all records with a `batchAmount` greater than 20.00"
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportBills(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of bills for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportBillsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportBills(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
- `status` (in, nin, eq, ne)
- `billNumber` (ct, nct, eq, ne)
- `billDate` (gt, ge, lt, le, eq, ne)
- `billDueDate` (gt, ge, lt, le, eq, ne)
- `vendorNumber` (ct, nct, eq, ne)
- `vendorName` (ct, nct, eq, ne)
- `ein` (ct, nct, eq, ne)
- `paymentMethod` (ct, nct, eq, ne)
- `paymentId` (ct, nct, eq, ne)
- `paymentgroup` (ct, nct, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: totalAmount(gt)=20  return all records with totalAmount greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportBillsOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of bills for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportBillsOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportBillsOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
- `status` (in, nin, eq, ne)
- `billNumber` (ct, nct, eq, ne)
- `billDate` (gt, ge, lt, le, eq, ne)
- `billDueDate` (gt, ge, lt, le, eq, ne)
- `vendorNumber` (ct, nct, eq, ne)
- `vendorName` (ct, nct, eq, ne)
- `ein` (ct, nct, eq, ne)
- `paymentMethod` (ct, nct, eq, ne)
- `paymentId` (ct, nct, eq, ne)
- `paymentgroup` (ct, nct, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: totalAmount(gt)=20  return all records with totalAmount greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportChargebacks(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of chargebacks and ACH returns for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportChargebacksRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportChargebacks(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
- `chargebackDate` (gt, ge, lt, le, eq, ne)
- `transId` (ne, eq, ct, nct)
- `method` (in, nin, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `reasonCode` (in, nin, eq, ne)
- `reason` (ct, nct, eq, ne)
- `caseNumber` (ct, nct, eq, ne)
- `status` (in, nin, eq, ne)
- `accountType` (in, nin, eq, ne)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq) *mandatory when entry=org*
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportChargebacksOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of chargebacks and ACH returns for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportChargebacksOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportChargebacksOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
- `chargebackDate` (gt, ge, lt, le, eq, ne)
- `transId` (ne, eq, ct, nct)
- `method` (in, nin, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `reasonCode` (in, nin, eq, ne)
- `reason` (ct, nct, eq, ne)
- `caseNumber` (ct, nct, eq, ne)
- `status` (in, nin, eq, ne)
- `accountType` (in, nin, eq, ne)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq) *mandatory when entry=org*
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportCustomers(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of customers for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportCustomersRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportCustomers(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

**List of field names accepted:**
- `createdDate` (gt, ge, lt, le, eq, ne)
- `customernumber` (ne, eq, ct, nct)
- `firstname` (ne, eq, ct, nct)
- `lastname` (ne, eq, ct, nct)
- `name` (ct, nct)
- `address` (ne, eq, ct, nct)
- `city` (ne, eq, ct, nct)
- `country` (ne, eq, ct, nct)
- `zip` (ne, eq, ct, nct)
- `state` (ne, eq, ct, nct)
- `shippingaddress` (ne, eq, ct, nct)
- `shippingcity` (ne, eq, ct, nct)
- `shippingcountry` (ne, eq, ct, nct)
- `shippingzip` (ne, eq, ct, nct)
- `shippingstate` (ne, eq, ct, nct)
- `phone` (ne, eq, ct, nct)
- `email` (ne, eq, ct, nct)
- `company` (ne, eq, ct, nct)
- `username` (ne, eq, ct, nct)
- `balance` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name
- `orgId` (eq) *mandatory when entry=org*
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

**List of comparison accepted - enclosed between parentheses:**
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

**List of parameters accepted:**
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

**Example:**
balance(gt)=20 return all records with balance greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportCustomersOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Exports a list of customers for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportCustomersOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportCustomersOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

**List of field names accepted:**
- `createdDate` (gt, ge, lt, le, eq, ne)
- `customernumber` (ne, eq, ct, nct)
- `firstname` (ne, eq, ct, nct)
- `lastname` (ne, eq, ct, nct)
- `name` (ct, nct)
- `address` (ne, eq, ct, nct)
- `city` (ne, eq, ct, nct)
- `country` (ne, eq, ct, nct)
- `zip` (ne, eq, ct, nct)
- `state` (ne, eq, ct, nct)
- `shippingaddress` (ne, eq, ct, nct)
- `shippingcity` (ne, eq, ct, nct)
- `shippingcountry` (ne, eq, ct, nct)
- `shippingzip` (ne, eq, ct, nct)
- `shippingstate` (ne, eq, ct, nct)
- `phone` (ne, eq, ct, nct)
- `email` (ne, eq, ct, nct)
- `company` (ne, eq, ct, nct)
- `username` (ne, eq, ct, nct)
- `balance` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name
- `orgId` (eq) *mandatory when entry=org*
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

**List of comparison accepted - enclosed between parentheses:**
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

**List of parameters accepted:**
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

**Example:**
balance(gt)=20 return all records with balance greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportInvoices(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export list of invoices for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportInvoicesRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportInvoices(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
 - `invoiceDate` (gt, ge, lt, le, eq, ne)
 - `dueDate` (gt, ge, lt, le, eq, ne)
 - `sentDate` (gt, ge, lt, le, eq, ne)
 - `frequency`  (in, nin,ne, eq)
 - `invoiceType`   (eq, ne)
 - `payTerms`   (in, nin, eq, ne)
 - `paypointId`  (ne, eq)
 - `totalAmount`  (gt, ge, lt, le, eq, ne)
 - `paidAmount`  (gt, ge, lt, le, eq, ne)
 - `status`   (in, nin, eq, ne)
 - `invoiceNumber`   (ct, nct, eq, ne)
 - `purchaseOrder`   (ct, nct, eq, ne)
 - `itemProductCode` (ct, nct)
 - `itemDescription` (ct, nct)
 - `customerFirstname`   (ct, nct, eq, ne)
 - `customerLastname`    (ct, nct, eq, ne)
 - `customerName`   (ct, nct)
 - `customerId`  (eq, ne)
 - `customerNumber`  (ct, nct, eq, ne)
 - `customerCompanyname`    (ct, nct, eq, ne)
 - `customerAddress` (ct, nct, eq, ne)
 - `customerCity`    (ct, nct, eq, ne)
 - `customerZip` (ct, nct, eq, ne)
 - `customerState` (ct, nct, eq, ne)
 - `customerCountry` (ct, nct, eq, ne)
 - `customerPhone` (ct, nct, eq, ne)
 - `customerEmail` (ct, nct, eq, ne)
 - `customerShippingAddress` (ct, nct, eq, ne)
 - `customerShippingCity` (ct, nct, eq, ne)
 - `customerShippingZip` (ct, nct, eq, ne)
 - `customerShippingState` (ct, nct, eq, ne)
 - `customerShippingCountry` (ct, nct, eq, ne)
 - `orgId`  (eq) 
 - `paylinkId`  (ne, eq)
 - `paypointLegal`  (ne, eq, ct, nct)
 - `paypointDba`  (ne, eq, ct, nct)
 - `orgName`  (ne, eq, ct, nct)
 - `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
 - eq or empty => equal
 - gt => greater than
 - ge => greater or equal
 - lt => less than
 - le => less or equal
 - ne => not equal
 - ct => contains
 - nct => not contains
 - in => inside array
 - nin => not inside array
 
List of parameters accepted:
 - `limitRecord` : max number of records for query (default="20", "0" or negative value for all)
 - `fromRecord` : initial record in query
 
Example: `totalAmount(gt)=20` returns all records with `totalAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportInvoicesOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of invoices for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportInvoicesOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportInvoicesOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
 - `invoiceDate` (gt, ge, lt, le, eq, ne)
 - `dueDate` (gt, ge, lt, le, eq, ne)
 - `sentDate` (gt, ge, lt, le, eq, ne)
 - `frequency` (in, nin,ne, eq)
 - `invoiceType` (eq, ne)
 - `payTerms` (in, nin, eq, ne)
 - `paypointId` (ne, eq)
 - `totalAmount` (gt, ge, lt, le, eq, ne)
 - `paidAmount` (gt, ge, lt, le, eq, ne)
 - `status` (in, nin, eq, ne)
 - `invoiceNumber` (ct, nct, eq, ne)
 - `purchaseOrder` (ct, nct, eq, ne)
 - `itemProductCode` (ct, nct)
 - `itemDescription` (ct, nct)
 - `customerFirstname` (ct, nct, eq, ne)
 - `customerLastname` (ct, nct, eq, ne)
 - `customerName` (ct, nct)
 - `customerId` (eq, ne)
 - `customerNumber` (ct, nct, eq, ne)
 - `customerCompanyname` (ct, nct, eq, ne)
 - `customerAddress` (ct, nct, eq, ne)
 - `customerCity` (ct, nct, eq, ne)
 - `customerZip` (ct, nct, eq, ne)
 - `customerState` (ct, nct, eq, ne)
 - `customerCountry` (ct, nct, eq, ne)
 - `customerPhone` (ct, nct, eq, ne)
 - `customerEmail` (ct, nct, eq, ne)
 - `customerShippingAddress` (ct, nct, eq, ne)
 - `customerShippingCity` (ct, nct, eq, ne)
 - `customerShippingZip` (ct, nct, eq, ne)
 - `customerShippingState` (ct, nct, eq, ne)
 - `customerShippingCountry` (ct, nct, eq, ne)
 - `orgId` (eq) 
 - `paylinkId` (ne, eq)
 - `paypointLegal` (ne, eq, ct, nct)
 - `paypointDba` (ne, eq, ct, nct)
 - `orgName` (ne, eq, ct, nct)
 - `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name
 
List of comparison accepted - enclosed between parentheses:
 - eq or empty => equal
 - gt => greater than
 - ge => greater or equal
 - lt => less than
 - le => less or equal
 - ne => not equal
 - ct => contains
 - nct => not contains
 - in => inside array
 - nin => not inside array
 
List of parameters accepted:
 - limitRecord : max number of records for query (default="20", "0" or negative value for all)
 - fromRecord : initial record in query
 
Example: totalAmount(gt)=20  return all records with totalAmount greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportOrganizations(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of child organizations (suborganizations) for a parent organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportOrganizationsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportOrganizations(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
- `name` (ct, nct, eq, ne)
- `type` (ne, eq)
- `contactName` (ct, nct, eq, ne)
- `contactTitle` (ct, nct, eq, ne)
- `contactEmail` (ct, nct, eq, ne)
- `contactPhone` (ct, nct, eq, ne)
- `city` (ct, nct, eq, ne)
- `state` (in, nin, eq, ne)
- `address` (ct, nct, eq, ne)
- `country` (ct, nct, eq, ne)
- `zip` (ct, nct, eq, ne)
- `hasBilling` any value greater than zero is taken as TRUE otherwise is FALSE
- `hasResidual` any value greater than zero is taken as TRUE otherwise is FALSE

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: name(ct)=hoa  return all records where name contains "hoa"
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportPayout(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of payouts and their statuses for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportPayoutRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportPayout(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `status` (in, nin, eq, ne)
- `transactionDate` (gt, ge, lt, le, eq, ne)
- `billNumber` (ct, nct)
- `vendorNumber` (ct, nct, eq, ne)
- `vendorName` (ct, nct, eq, ne)
- `paymentMethod` (ct, nct, eq, ne)
- `paymentId` (ct, nct, eq, ne)
- `paymentgroup` (ct, nct, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: totalAmount(gt)=20 return all records with totalAmount greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportPayoutOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of payouts and their details for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportPayoutOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportPayoutOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `status` (in, nin, eq, ne)
- `transactionDate` (gt, ge, lt, le, eq, ne)
- `billNumber` (ct, nct)
- `vendorNumber` (ct, nct, eq, ne)
- `vendorName` (ct, nct, eq, ne)
- `paymentMethod` (ct, nct, eq, ne)
- `paymentId` (ct, nct, eq, ne)
- `paymentgroup` (ct, nct, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: totalAmount(gt)=20 return all records with totalAmount greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportPaypoints(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of paypoints in an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportPaypointsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportPaypoints(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `createdAt` (gt, ge, lt, le, eq, ne)
- `startDate` (gt, ge, lt, le, eq, ne)
- `dbaname` (ct, nct)
- `legalname` (ct, nct)
- `ein` (ct, nct)
- `address` (ct, nct)
- `city` (ct, nct)
- `state` (ct, nct)
- `phone` (ct, nct)
- `mcc` (ct, nct)
- `owntype` (ct, nct)
- `ownerName` (ct, nct)
- `contactName` (ct, nct)
- `orgParentname` (ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `dbaname(ct)=hoa` returns all records with `dbaname` containing "hoa"
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportSettlements(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of settled transactions for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportSettlementsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportSettlements(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `settlementDate` (gt, ge, lt, le, eq, ne)
- `transId` (ne, eq, ct, nct)
- `gatewayTransId` (ne, eq, ct, nct)
- `method` (in, nin, eq, ne)
- `settledAmount` (gt, ge, lt, le, eq, ne)
- `operation` (in, nin, eq, ne)
- `source` (in, nin, eq, ne)
- `batchNumber` (ct, nct, eq, ne)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq) *mandatory when entry=org*
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: `settledAmount(gt)=20` returns all records with a `settledAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportSettlementsOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of settled transactions for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportSettlementsOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportSettlementsOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `settlementDate` (gt, ge, lt, le, eq, ne)
- `transId` (ne, eq, ct, nct)
- `gatewayTransId` (ne, eq, ct, nct)
- `method` (in, nin, eq, ne)
- `settledAmount` (gt, ge, lt, le, eq, ne)
- `operation` (in, nin, eq, ne)
- `source` (in, nin, eq, ne)
- `batchNumber` (ct, nct, eq, ne)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq) *mandatory when entry=org*
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord: max number of records for query (default="20", "0" or negative value for all)
- fromRecord: initial record in query

Example: `settledAmount(gt)=20` returns all records with a `settledAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportSubscriptions(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of subscriptions for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportSubscriptionsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportSubscriptions(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `startDate` (gt, ge, lt, le, eq, ne)
- `endDate` (gt, ge, lt, le, eq, ne)
- `nextDate` (gt, ge, lt, le, eq, ne)
- `frequency` (in, nin, ne, eq)
- `method` (in, nin, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `feeAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `untilcancelled` (eq, ne)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq) 
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportSubscriptionsOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of subscriptions for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportSubscriptionsOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportSubscriptionsOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `startDate` (gt, ge, lt, le, eq, ne)
- `endDate` (gt, ge, lt, le, eq, ne)
- `nextDate` (gt, ge, lt, le, eq, ne)
- `frequency` (in, nin, ne, eq)
- `method` (in, nin, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `feeAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `untilcancelled` (eq, ne)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq) 
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportTransactions(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of transactions for an entrypoint in a file in XLXS or CSV format. Use filters to limit results. If you don't specify a date range in the request, the last two months of data are returned.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportTransactionsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportTransactions(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
- `transactionDate` (gt, ge, lt, le, eq, ne)
- `transId` (ne, eq, ct, nct)
- `gatewayTransId` (ne, eq, ct, nct)
- `orderId` (ne, eq)
- `idTrans` (ne, eq)
- `orgId` (ne, eq)
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `method` (in, nin, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `feeAmount` (gt, ge, lt, le, eq, ne)
- `operation` (in, nin, eq, ne)
- `source` (in, nin, eq, ne)
- `status` (in, nin, eq, ne)
- `settlementStatus` (in, nin, eq, ne)
- `batchNumber` (nct, ct)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportTransactionsOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of transactions for an org in a file in XLSX or CSV format. Use filters to limit results. If you don't specify a date range in the request, the last two months of data are returned.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportTransactionsOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportTransactionsOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
- `transactionDate` (gt, ge, lt, le, eq, ne)
- `transId` (ne, eq, ct, nct)
- `gatewayTransId` (ne, eq, ct, nct)
- `orderId` (ne, eq)
- `idTrans` (ne, eq)
- `orgId` (ne, eq)
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `method` (in, nin, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `feeAmount` (gt, ge, lt, le, eq, ne)
- `operation` (in, nin, eq, ne)
- `source` (in, nin, eq, ne)
- `status` (in, nin, eq, ne)
- `settlementStatus` (in, nin, eq, ne)
- `batchNumber` (nct, ct)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportTransferDetails(Format, Entry, TransferId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of transfer details for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportTransferDetailsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Export.ExportTransferDetails(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        1000000,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**transferId:** `int64` — Transfer identifier.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:

  - `grossAmount` (gt, ge, lt, le, eq, ne)

  - `chargeBackAmount` (gt, ge, lt, le, eq, ne)

  - `returnedAmount` (gt, ge, lt, le, eq, ne)

  - `billingFeeAmount` (gt, ge, lt, le, eq, ne)

  - `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)

  - `netFundedAmount` (gt, ge, lt, le, eq, ne)

  - `adjustmentAmount` (gt, ge, lt, le, eq, ne)

  - `transactionId` (eq, ne, in, nin)

  - `category` (eq, ne, ct, nct)

  - `type` (eq, ne, in, nin)

  - `method` (eq, ne, in, nin)
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportTransfers(Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a list of transfers for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportTransfersRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Export.ExportTransfers(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help. 

List of field names accepted:
  - `transferDate` (gt, ge, lt, le, eq, ne)

  - `grossAmount` (gt, ge, lt, le, eq, ne)

  - `chargeBackAmount` (gt, ge, lt, le, eq, ne)

  - `returnedAmount` (gt, ge, lt, le, eq, ne)

  - `billingFeeAmount` (gt, ge, lt, le, eq, ne)

  - `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)

  - `netFundedAmount` (gt, ge, lt, le, eq, ne)

  - `adjustmentAmount` (gt, ge, lt, le, eq, ne)

  - `processor` (ne, eq, ct, nct)

  - `transferStatus` (ne, eq, in, nin)

  - `batchNumber` (ne, eq, ct, nct)

  - `batchId` (ne, eq, in, nin)
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportVendors(Format, Entry) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of vendors for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportVendorsRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportVendors(
        context.TODO(),
        "8cfec329267",
        payabli.ExportFormat1Csv.Ptr(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `method` (in, nin, eq, ne)
- `enrollmentStatus` (in, nin, eq, ne)
- `status` (in, nin, eq, ne)
- `vendorNumber` (ct, nct, eq, ne)
- `name` (ct, nct, eq, ne)
- `ein` (ct, nct, eq, ne)
- `phone` (ct, nct, eq, ne)
- `email` (ct, nct, eq, ne)
- `address` (ct, nct, eq, ne)
- `city` (ct, nct, eq, ne)
- `state` (ct, nct, eq, ne)
- `country` (ct, nct, eq, ne)
- `zip` (ct, nct, eq, ne)
- `mcc` (ct, nct, eq, ne)
- `locationCode` (ct, nct, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Export.ExportVendorsOrg(Format, OrgId) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a list of vendors for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ExportVendorsOrgRequest{
        ColumnsExport: payabli.String(
            "BatchDate:Batch_Date,PaypointName:Legal_name",
        ),
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            1000,
        ),
    }
client.Export.ExportVendorsOrg(
        context.TODO(),
        payabli.ExportFormat1Csv.Ptr(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**format:** `*payabli.ExportFormat1` — Format for the export, either XLSX or CSV. 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**columnsExport:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — The number of records to return for the query. The maximum is 30,000 records. When this parameter isn't sent, the API returns up to 25,000 records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `method` (in, nin, eq, ne)
- `enrollmentStatus` (in, nin, eq, ne)
- `status` (in, nin, eq, ne)
- `vendorNumber` (ct, nct, eq, ne)
- `name` (ct, nct, eq, ne)
- `ein` (ct, nct, eq, ne)
- `phone` (ct, nct, eq, ne)
- `email` (ct, nct, eq, ne)
- `address` (ct, nct, eq, ne)
- `city` (ct, nct, eq, ne)
- `state` (ct, nct, eq, ne)
- `country` (ct, nct, eq, ne)
- `zip` (ct, nct, eq, ne)
- `mcc` (ct, nct, eq, ne)
- `locationCode` (ct, nct, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## HostedPaymentPages
<details><summary><code>client.HostedPaymentPages.LoadPage(Entry, Subdomain) -> *payabli.PayabliPages</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Loads all of a payment page's details including `pageIdentifier` and `validationCode`. This endpoint requires an `application` API token.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.HostedPaymentPages.LoadPage(
        context.TODO(),
        "8cfec329267",
        "pay-your-fees-1",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**subdomain:** `string` — Payment page identifier. The subdomain value is the last part of the payment page URL. For example, in`https://paypages-sandbox.payabli.com/513823dc10/pay-your-fees-1`, the subdomain is `pay-your-fees-1`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.HostedPaymentPages.NewPage(Entry, request) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>


Creates a new payment page for a paypoint. 
Note: this operation doesn't create a new paypoint, just a payment page for an existing paypoint. Paypoints are created by the Payabli team when a boarding application is approved.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.NewPageRequest{
        IdempotencyKey: payabli.String(
            "6B29FC40-CA47-1067-B31D-00DD010662DA",
        ),
        Body: &payabli.PayabliPages{},
    }
client.HostedPaymentPages.NewPage(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.PayabliPages` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.HostedPaymentPages.SavePage(Entry, Subdomain, request) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates a payment page in a paypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.PayabliPages{}
client.HostedPaymentPages.SavePage(
        context.TODO(),
        "8cfec329267",
        "pay-your-fees-1",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**subdomain:** `string` — Payment page identifier. The subdomain value is the last part of the payment page URL. For example, in`https://paypages-sandbox.payabli.com/513823dc10/pay-your-fees-1`, the subdomain is `pay-your-fees-1`.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.PayabliPages` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Import
<details><summary><code>client.Import.ImportBills(Entry, request) -> *payabli.PayabliApiResponseImport</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Import a list of bills from a CSV file. See the [Import Guide](/developers/developer-guides/bills-add#import-bills) for more help and an example file.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ImportBillsRequest{}
client.Import.ImportBills(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Import.ImportCustomer(Entry, request) -> *payabli.PayabliApiResponseImport</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Import a list of customers from a CSV file. See the [Import Guide](/developers/developer-guides/entities-customers#import-customers) for more help and example files.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ImportCustomerRequest{}
client.Import.ImportCustomer(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entrypointfield` 
    
</dd>
</dl>

<dl>
<dd>

**replaceExisting:** `*int` — Flag indicating to replace existing customer with a new record. Possible values: 0 (do not replace), 1 (replace). Default is 0
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Import.ImportVendor(Entry, request) -> *payabli.PayabliApiResponseImport</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Import a list of vendors from a CSV file. See the [Import Guide](/developers/developer-guides/entities-vendors#import-vendors) for more help and example files.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ImportVendorRequest{}
client.Import.ImportVendor(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entrypointfield` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Invoice
<details><summary><code>client.Invoice.AddInvoice(Entry, request) -> *payabli.InvoiceResponseWithoutData</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates an invoice in an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddInvoiceRequest{
        Body: &payabli.InvoiceDataRequest{
            CustomerData: &payabli.PayorDataRequest{
                FirstName: payabli.String(
                    "Tamara",
                ),
                LastName: payabli.String(
                    "Bagratoni",
                ),
                CustomerNumber: payabli.String(
                    "3",
                ),
            },
            InvoiceData: &payabli.BillData{
                Items: []*payabli.BillItem{
                    &payabli.BillItem{
                        ItemProductName: payabli.String(
                            "Adventure Consult",
                        ),
                        ItemDescription: payabli.String(
                            "Consultation for Georgian tours",
                        ),
                        ItemCost: 100,
                        ItemQty: payabli.Int(
                            1,
                        ),
                        ItemMode: payabli.Int(
                            1,
                        ),
                        ItemTotalAmount: payabli.Float64(
                            1,
                        ),
                    },
                    &payabli.BillItem{
                        ItemProductName: payabli.String(
                            "Deposit ",
                        ),
                        ItemDescription: payabli.String(
                            "Deposit for trip planning",
                        ),
                        ItemCost: 882.37,
                        ItemQty: payabli.Int(
                            1,
                        ),
                        ItemTotalAmount: payabli.Float64(
                            1,
                        ),
                    },
                },
                InvoiceDate: payabli.Time(
                    payabli.MustParseDate(
                        "2025-10-19",
                    ),
                ),
                InvoiceType: payabli.Int(
                    0,
                ),
                InvoiceStatus: payabli.Int(
                    1,
                ),
                Frequency: payabli.FrequencyOneTime.Ptr(),
                InvoiceAmount: payabli.Float64(
                    982.37,
                ),
                Discount: payabli.Float64(
                    10,
                ),
                InvoiceNumber: payabli.String(
                    "INV-3",
                ),
            },
        },
    }
client.Invoice.AddInvoice(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**forceCustomerCreation:** `*payabli.ForceCustomerCreation` 
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.InvoiceDataRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.DeleteAttachedFromInvoice(IdInvoice, Filename) -> *payabli.InvoiceResponseWithoutData</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes an invoice that's attached to a file.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Invoice.DeleteAttachedFromInvoice(
        context.TODO(),
        "0_Bill.pdf",
        23548884,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idInvoice:** `int` — Invoice ID
    
</dd>
</dl>

<dl>
<dd>

**filename:** `string` 

The filename in Payabli. Filename is `zipName` in response to a request to `/api/Invoice/{idInvoice}`. Here, the filename is `0_Bill.pdf``. 
"DocumentsRef": {
  "zipfile": "inva_269.zip",
  "filelist": [
    {
      "originalName": "Bill.pdf",
      "zipName": "0_Bill.pdf",
      "descriptor": null
    }
  ]
}
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.DeleteInvoice(IdInvoice) -> *payabli.InvoiceResponseWithoutData</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a single invoice from an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Invoice.DeleteInvoice(
        context.TODO(),
        23548884,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idInvoice:** `int` — Invoice ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.EditInvoice(IdInvoice, request) -> *payabli.InvoiceResponseWithoutData</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates details for a single invoice in an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.EditInvoiceRequest{
        Body: &payabli.InvoiceDataRequest{
            InvoiceData: &payabli.BillData{
                Items: []*payabli.BillItem{
                    &payabli.BillItem{
                        ItemProductName: payabli.String(
                            "Deposit",
                        ),
                        ItemDescription: payabli.String(
                            "Deposit for trip planning",
                        ),
                        ItemCost: 882.37,
                        ItemQty: payabli.Int(
                            1,
                        ),
                    },
                },
                InvoiceDate: payabli.Time(
                    payabli.MustParseDate(
                        "2025-10-19",
                    ),
                ),
                InvoiceAmount: payabli.Float64(
                    982.37,
                ),
                InvoiceNumber: payabli.String(
                    "INV-6",
                ),
            },
        },
    }
client.Invoice.EditInvoice(
        context.TODO(),
        332,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idInvoice:** `int` — Invoice ID
    
</dd>
</dl>

<dl>
<dd>

**forceCustomerCreation:** `*bool` — When `true`, the request creates a new customer record, regardless of whether customer identifiers match an existing customer.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.InvoiceDataRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.GetAttachedFileFromInvoice(IdInvoice, Filename) -> *payabli.FileContent</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a file attached to an invoice.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.GetAttachedFileFromInvoiceRequest{}
client.Invoice.GetAttachedFileFromInvoice(
        context.TODO(),
        1,
        "filename",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idInvoice:** `int` — Invoice ID
    
</dd>
</dl>

<dl>
<dd>

**filename:** `string` 

The filename in Payabli. Filename is `zipName` in the response to a request to `/api/Invoice/{idInvoice}`. Here, the filename is `0_Bill.pdf``. 
```
  "DocumentsRef": {
    "zipfile": "inva_269.zip",
    "filelist": [
      {
        "originalName": "Bill.pdf",
        "zipName": "0_Bill.pdf",
        "descriptor": null
      }
    ]
  }
  ```
    
</dd>
</dl>

<dl>
<dd>

**returnObject:** `*bool` — When `true`, the request returns the file content as a Base64-encoded string.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.GetInvoice(IdInvoice) -> *payabli.GetInvoiceRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a single invoice by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Invoice.GetInvoice(
        context.TODO(),
        23548884,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idInvoice:** `int` — Invoice ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.GetInvoiceNumber(Entry) -> *payabli.InvoiceNumberResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves the next available invoice number for a paypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Invoice.GetInvoiceNumber(
        context.TODO(),
        "8cfec329267",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.ListInvoices(Entry) -> *payabli.QueryInvoiceResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of invoices for an entrypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListInvoicesRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Invoice.ListInvoices(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:

- `invoiceDate` (gt, ge, lt, le, eq, ne)
- `dueDate` (gt, ge, lt, le, eq, ne)
- `sentDate` (gt, ge, lt, le, eq, ne)
- `frequency` (in, nin,ne, eq)
- `invoiceType` (eq, ne)
- `payTerms` (in, nin, eq, ne)
- `paypointId` (ne, eq)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `paidAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `invoiceNumber` (ct, nct, eq, ne)
- `purchaseOrder` (ct, nct, eq, ne)
- `itemProductCode` (ct, nct)
- `itemDescription` (ct, nct)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq)
- `paylinkId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:
  
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: totalAmount(gt)=20 return all records with totalAmount greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.ListInvoicesOrg(OrgId) -> *payabli.QueryInvoiceResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of invoices for an org. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListInvoicesOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Invoice.ListInvoicesOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:

- `invoiceDate` (gt, ge, lt, le, eq, ne)
- `dueDate` (gt, ge, lt, le, eq, ne)
- `sentDate` (gt, ge, lt, le, eq, ne)
- `frequency` (in, nin,ne, eq)
- `invoiceType` (eq, ne)
- `payTerms` (in, nin, eq, ne)
- `paypointId` (ne, eq)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `paidAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `invoiceNumber` (ct, nct, eq, ne)
- `purchaseOrder` (ct, nct, eq, ne)
- `itemProductCode` (ct, nct)
- `itemDescription` (ct, nct)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq)
- `paylinkId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name

List of comparison accepted - enclosed between parentheses:

- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: totalAmount(gt)=20 return all records with totalAmount greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.SendInvoice(IdInvoice) -> *payabli.SendInvoiceResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Sends an invoice from an entrypoint via email.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.SendInvoiceRequest{
        Attachfile: payabli.Bool(
            true,
        ),
        Mail2: payabli.String(
            "tamara@example.com",
        ),
    }
client.Invoice.SendInvoice(
        context.TODO(),
        23548884,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idInvoice:** `int` — Invoice ID
    
</dd>
</dl>

<dl>
<dd>

**attachfile:** `*bool` — When `true`, attaches a PDF version of invoice to the email.
    
</dd>
</dl>

<dl>
<dd>

**mail2:** `*string` — Email address where the invoice will be sent to. If this parameter isn't included, Payabli uses the email address on file for the customer owner of the invoice.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Invoice.GetInvoicePdf(IdInvoice) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export a single invoice in PDF format.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Invoice.GetInvoicePdf(
        context.TODO(),
        23548884,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idInvoice:** `int` — Invoice ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## LineItem
<details><summary><code>client.LineItem.AddItem(Entry, request) -> *payabli.PayabliApiResponse6</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Adds products and services to an entrypoint's catalog. These are used as line items for invoicing and transactions. In the response, "responseData" displays the item's code.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddItemRequest{
        Body: &payabli.LineItem{
            ItemProductCode: payabli.String(
                "M-DEPOSIT",
            ),
            ItemProductName: payabli.String(
                "Materials deposit",
            ),
            ItemDescription: payabli.String(
                "Deposit for materials",
            ),
            ItemCommodityCode: payabli.String(
                "010",
            ),
            ItemUnitOfMeasure: payabli.String(
                "SqFt",
            ),
            ItemCost: 12.45,
            ItemQty: 1,
            ItemMode: payabli.Int(
                0,
            ),
        },
    }
client.LineItem.AddItem(
        context.TODO(),
        "47cae3d74",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*string` — A unique ID you can include to prevent duplicating objects or transactions if a request is sent more than once. This key isn't generated in Payabli, you must generate it yourself. 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.LineItem` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.LineItem.DeleteItem(LineItemId) -> *payabli.DeleteItemResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes an item.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.LineItem.DeleteItem(
        context.TODO(),
        700,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**lineItemId:** `int` — ID for the line item (also known as a product, service, or item).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.LineItem.GetItem(LineItemId) -> *payabli.LineItemQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Gets an item by ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.LineItem.GetItem(
        context.TODO(),
        700,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**lineItemId:** `int` — ID for the line item (also known as a product, service, or item).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.LineItem.ListLineItems(Entry) -> *payabli.QueryResponseItems</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a list of line items and their details from an entrypoint. Line items are also known as items, products, and services. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListLineItemsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.LineItem.ListLineItems(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20

</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:

  - `categories` (ct, nct)
  - `code` (ne, eq, ct, nct)
  - `commodityCode` (ne, eq, ct, nct)
  - `createdDate` (gt, ge, lt, le, eq, ne)
  - `description` (ne, eq, ct, nct)
  - `externalPaypointID` (ct, nct, ne, eq)
  - `mode` (eq, ne)
  - `name` (ne, eq, ct, nct)
  - `orgName` (ne, eq, ct, nct)
  - `paypointDba` (ne, eq, ct, nct)
  - `paypointId` (ne, eq)
  - `paypointLegal` (ne, eq, ct, nct)
  - `quantity` (gt, ge, lt, le, eq, ne)
  - `uom` (ne, eq, ct, nct)
  - `updatedDate` (gt, ge, lt, le, eq, ne)
  - `value` (gt, ge, lt, le, eq, ne)

List of comparison accepted - enclosed between parentheses:

- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: name(ct)=john return all records with name containing john
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.LineItem.UpdateItem(LineItemId, request) -> *payabli.PayabliApiResponse6</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates an item.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.LineItem{
        ItemCost: 12.45,
        ItemQty: 1,
    }
client.LineItem.UpdateItem(
        context.TODO(),
        700,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**lineItemId:** `int` — ID for the line item (also known as a product, service, or item).
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.LineItem` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## MoneyIn
<details><summary><code>client.MoneyIn.Authorize(request) -> *payabli.AuthResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Authorize a card transaction. This returns an authorization code and reserves funds for the merchant. Authorized transactions aren't flagged for settlement until [captured](/api-reference/moneyin/capture-an-authorized-transaction).

**Note**: Only card transactions can be authorized. This endpoint can't be used for ACH transactions.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RequestPaymentAuthorize{
        Body: &payabli.TransRequestBody{
            CustomerData: &payabli.PayorDataRequest{
                CustomerId: payabli.Int64(
                    4440,
                ),
            },
            EntryPoint: payabli.String(
                "f743aed24a",
            ),
            Ipaddress: payabli.String(
                "255.255.255.255",
            ),
            PaymentDetails: &payabli.PaymentDetail{
                ServiceFee: payabli.Float64(
                    0,
                ),
                TotalAmount: 100,
            },
            PaymentMethod: &payabli.PaymentMethod{
                PayMethodCredit: &payabli.PayMethodCredit{
                    Cardcvv: payabli.String(
                        "999",
                    ),
                    Cardexp: "02/27",
                    CardHolder: payabli.String(
                        "John Cassian",
                    ),
                    Cardnumber: "4111111111111111",
                    Cardzip: payabli.String(
                        "12345",
                    ),
                    Initiator: payabli.String(
                        "payor",
                    ),
                },
            },
        },
    }
client.MoneyIn.Authorize(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**forceCustomerCreation:** `*payabli.ForceCustomerCreation` 
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.TransRequestBody` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.Capture(TransId, Amount) -> *payabli.CaptureResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

<Warning>
  This endpoint is deprecated and will be sunset on November 24, 2025. Migrate to [POST `/capture/{transId}`](/api-reference/moneyin/capture-an-authorized-transaction)`.
</Warning>
  
  Capture an [authorized
transaction](/api-reference/moneyin/authorize-a-transaction) to complete the transaction and move funds from the customer to merchant account.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyIn.Capture(
        context.TODO(),
        "10-7d9cd67d-2d5d-4cd7-a1b7-72b8b201ec13",
        0,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>

<dl>
<dd>

**amount:** `float64` — Amount to be captured. The amount can't be greater the original total amount of the transaction. `0` captures the total amount authorized in the transaction. Partial captures aren't supported.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.CaptureAuth(TransId, request) -> *payabli.CaptureResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Capture an [authorized transaction](/api-reference/moneyin/authorize-a-transaction) to complete the transaction and move funds from the customer to merchant account. 

You can use this endpoint to capture both full and partial amounts of the original authorized transaction. See [Capture an authorized transaction](/developers/developer-guides/pay-in-auth-and-capture) for more information about this endpoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.CaptureRequest{
        PaymentDetails: &payabli.CapturePaymentDetails{
            TotalAmount: 105,
            ServiceFee: payabli.Float64(
                5,
            ),
        },
    }
client.MoneyIn.CaptureAuth(
        context.TODO(),
        "10-7d9cd67d-2d5d-4cd7-a1b7-72b8b201ec13",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.CaptureRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.Credit(request) -> *payabli.PayabliApiResponse0</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Make a temporary microdeposit in a customer account to verify the customer's ownership and access to the target account. Reverse the microdeposit with `reverseCredit`.

This feature must be enabled by Payabli on a per-merchant basis. Contact support for help. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RequestCredit{
        IdempotencyKey: payabli.String(
            "6B29FC40-CA47-1067-B31D-00DD010662DA",
        ),
        CustomerData: &payabli.PayorDataRequest{
            BillingAddress1: payabli.String(
                "5127 Linkwood ave",
            ),
            CustomerNumber: payabli.String(
                "100",
            ),
        },
        Entrypoint: payabli.String(
            "my-entrypoint",
        ),
        PaymentDetails: &payabli.PaymentDetailCredit{
            ServiceFee: payabli.Float64(
                0,
            ),
            TotalAmount: 1,
        },
        PaymentMethod: &payabli.RequestCreditPaymentMethod{
            AchAccount: payabli.String(
                "88354454",
            ),
            AchAccountType: payabli.AchaccounttypeChecking.Ptr(),
            AchHolder: payabli.String(
                "John Smith",
            ),
            AchRouting: payabli.String(
                "021000021",
            ),
        },
    }
client.MoneyIn.Credit(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**forceCustomerCreation:** `*payabli.ForceCustomerCreation` 
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**accountId:** `*payabli.Accountid` 
    
</dd>
</dl>

<dl>
<dd>

**customerData:** `*payabli.PayorDataRequest` — Object describing the customer/payor.
    
</dd>
</dl>

<dl>
<dd>

**entrypoint:** `*payabli.Entrypointfield` 
    
</dd>
</dl>

<dl>
<dd>

**orderDescription:** `*payabli.Orderdescription` 
    
</dd>
</dl>

<dl>
<dd>

**orderId:** `*payabli.OrderId` 
    
</dd>
</dl>

<dl>
<dd>

**paymentDetails:** `*payabli.PaymentDetailCredit` 
    
</dd>
</dl>

<dl>
<dd>

**paymentMethod:** `*payabli.RequestCreditPaymentMethod` — Object describing the ACH payment method to use for transaction.
    
</dd>
</dl>

<dl>
<dd>

**source:** `*payabli.Source` 
    
</dd>
</dl>

<dl>
<dd>

**subdomain:** `*payabli.Subdomain` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.Details(TransId) -> *payabli.TransactionQueryRecordsCustomer</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a processed transaction's details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyIn.Details(
        context.TODO(),
        "45-as456777hhhhhhhhhh77777777-324",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.Getpaid(request) -> *payabli.PayabliApiResponseGetPaid</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Make a single transaction. This method authorizes and captures a payment in one step.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RequestPayment{
        Body: &payabli.TransRequestBody{
            CustomerData: &payabli.PayorDataRequest{
                CustomerId: payabli.Int64(
                    4440,
                ),
            },
            EntryPoint: payabli.String(
                "f743aed24a",
            ),
            Ipaddress: payabli.String(
                "255.255.255.255",
            ),
            PaymentDetails: &payabli.PaymentDetail{
                ServiceFee: payabli.Float64(
                    0,
                ),
                TotalAmount: 100,
            },
            PaymentMethod: &payabli.PaymentMethod{
                PayMethodCredit: &payabli.PayMethodCredit{
                    Cardcvv: payabli.String(
                        "999",
                    ),
                    Cardexp: "02/27",
                    CardHolder: payabli.String(
                        "John Cassian",
                    ),
                    Cardnumber: "4111111111111111",
                    Cardzip: payabli.String(
                        "12345",
                    ),
                    Initiator: payabli.String(
                        "payor",
                    ),
                },
            },
        },
    }
client.MoneyIn.Getpaid(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**achValidation:** `*payabli.AchValidation` 
    
</dd>
</dl>

<dl>
<dd>

**forceCustomerCreation:** `*payabli.ForceCustomerCreation` 
    
</dd>
</dl>

<dl>
<dd>

**includeDetails:** `*bool` — When `true`, transactionDetails object is returned in the response. See a full example of the `transactionDetails` object in the [Transaction integration guide](/developers/developer-guides/money-in-transaction-add#includedetailstrue-response).
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**validationCode:** `*string` — Value obtained from user when an API generated CAPTCHA is used in payment page
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.TransRequestBody` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.Reverse(TransId, Amount) -> *payabli.ReverseResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A reversal either refunds or voids a transaction independent of the transaction's settlement status. Send a reversal request for a transaction, and Payabli automatically determines whether it's a refund or void. You don't need to know whether the transaction is settled or not.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyIn.Reverse(
        context.TODO(),
        0,
        "10-3ffa27df-b171-44e0-b251-e95fbfc7a723",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>

<dl>
<dd>

**amount:** `float64` 


Amount to reverse from original transaction, minus any service fees charged on the original transaction.

The amount provided can't be greater than the original total amount of the transaction, minus service fees. For example, if a transaction was $90 plus a $10 service fee, you can reverse up to $90. 

An amount equal to zero will refunds the total amount authorized minus any service fee.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.Refund(TransId, Amount) -> *payabli.RefundResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Refund a transaction that has settled and send money back to the account holder. If a transaction hasn't been settled, void it instead.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyIn.Refund(
        context.TODO(),
        0,
        "10-3ffa27df-b171-44e0-b251-e95fbfc7a723",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>

<dl>
<dd>

**amount:** `float64` 


Amount to refund from original transaction, minus any service fees charged on the original transaction. 

The amount provided can't be greater than the original total amount of the transaction, minus service fees. For example, if a transaction was \$90 plus a \$10 service fee, you can refund up to \$90.

An amount equal to zero will refund the total amount authorized minus any service fee.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.RefundWithInstructions(TransId, request) -> *payabli.RefundWithInstructionsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Refunds a settled transaction with split instructions.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RequestRefund{
        IdempotencyKey: payabli.String(
            "8A29FC40-CA47-1067-B31D-00DD010662DB",
        ),
        Source: payabli.String(
            "api",
        ),
        OrderDescription: payabli.String(
            "Materials deposit",
        ),
        Amount: payabli.Float64(
            100,
        ),
        RefundDetails: &payabli.RefundDetail{
            SplitRefunding: []*payabli.SplitFundingRefundContent{
                &payabli.SplitFundingRefundContent{
                    OriginationEntryPoint: payabli.String(
                        "7f1a381696",
                    ),
                    AccountId: payabli.String(
                        "187-342",
                    ),
                    Description: payabli.String(
                        "Refunding undelivered materials",
                    ),
                    Amount: payabli.Float64(
                        60,
                    ),
                },
                &payabli.SplitFundingRefundContent{
                    OriginationEntryPoint: payabli.String(
                        "7f1a381696",
                    ),
                    AccountId: payabli.String(
                        "187-343",
                    ),
                    Description: payabli.String(
                        "Refunding deposit for undelivered materials",
                    ),
                    Amount: payabli.Float64(
                        40,
                    ),
                },
            },
        },
    }
client.MoneyIn.RefundWithInstructions(
        context.TODO(),
        "10-3ffa27df-b171-44e0-b251-e95fbfc7a723",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**amount:** `*float64` 


Amount to refund from original transaction, minus any service fees charged on the original transaction. 

The amount provided can't be greater than the original total amount of the transaction, minus service fees. For example, if a transaction was $90 plus a $10 service fee, you can refund up to $90. 

An amount equal to zero will refund the total amount authorized minus any service fee.
    
</dd>
</dl>

<dl>
<dd>

**ipaddress:** `*payabli.IpAddress` 
    
</dd>
</dl>

<dl>
<dd>

**orderDescription:** `*payabli.Orderdescription` 
    
</dd>
</dl>

<dl>
<dd>

**orderId:** `*payabli.OrderId` 
    
</dd>
</dl>

<dl>
<dd>

**refundDetails:** `*payabli.RefundDetail` 
    
</dd>
</dl>

<dl>
<dd>

**source:** `*payabli.Source` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.ReverseCredit(TransId) -> *payabli.PayabliApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Reverse microdeposits that are used to verify customer account ownership and access. The `transId` value is returned in the success response for the original credit transaction made with `api/MoneyIn/makecredit`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyIn.ReverseCredit(
        context.TODO(),
        "45-as456777hhhhhhhhhh77777777-324",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.SendReceipt2Trans(TransId) -> *payabli.ReceiptResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Send a payment receipt for a transaction.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.SendReceipt2TransRequest{
        Email: payabli.String(
            "example@email.com",
        ),
    }
client.MoneyIn.SendReceipt2Trans(
        context.TODO(),
        "45-as456777hhhhhhhhhh77777777-324",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>

<dl>
<dd>

**email:** `*string` 

Email address where the payment receipt should be sent. 

If not provided, the email address on file for the user owner of the transaction is used.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.Validate(request) -> *payabli.ValidateResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Validates a card number without running a transaction or authorizing a charge.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RequestPaymentValidate{
        IdempotencyKey: payabli.String(
            "6B29FC40-CA47-1067-B31D-00DD010662DA",
        ),
        EntryPoint: "entry132",
        PaymentMethod: &payabli.RequestPaymentValidatePaymentMethod{
            Method: payabli.RequestPaymentValidatePaymentMethodMethodCard,
            Cardnumber: "4360000001000005",
            Cardexp: "12/29",
            Cardzip: "14602-8328",
            CardHolder: "Dianne Becker-Smith",
        },
    }
client.MoneyIn.Validate(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**accountId:** `*payabli.Accountid` 
    
</dd>
</dl>

<dl>
<dd>

**entryPoint:** `payabli.Entrypointfield` 
    
</dd>
</dl>

<dl>
<dd>

**orderDescription:** `*payabli.Orderdescription` 
    
</dd>
</dl>

<dl>
<dd>

**orderId:** `*payabli.OrderId` 
    
</dd>
</dl>

<dl>
<dd>

**paymentMethod:** `*payabli.RequestPaymentValidatePaymentMethod` — Object describing payment method to use for transaction.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyIn.Void(TransId) -> *payabli.VoidResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a transaction that hasn't been settled yet. Voiding non-captured authorizations prevents future captures. If a transaction has been settled, refund it instead.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyIn.Void(
        context.TODO(),
        "10-3ffa27df-b171-44e0-b251-e95fbfc7a723",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## MoneyOut
<details><summary><code>client.MoneyOut.AuthorizeOut(request) -> *payabli.AuthCapturePayoutResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Authorizes transaction for payout. Authorized transactions aren't flagged for settlement until captured. Use `referenceId` returned in the response to capture the transaction. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.MoneyOutTypesRequestOutAuthorize{
        Body: &payabli.AuthorizePayoutBody{
            EntryPoint: "48acde49",
            InvoiceData: []*payabli.RequestOutAuthorizeInvoiceData{
                &payabli.RequestOutAuthorizeInvoiceData{
                    BillId: payabli.Int64(
                        54323,
                    ),
                },
            },
            OrderDescription: payabli.String(
                "Window Painting",
            ),
            PaymentDetails: &payabli.RequestOutAuthorizePaymentDetails{
                TotalAmount: payabli.Float64(
                    47,
                ),
                Unbundled: payabli.Bool(
                    false,
                ),
            },
            PaymentMethod: &payabli.AuthorizePaymentMethod{
                Method: "managed",
            },
            VendorData: &payabli.RequestOutAuthorizeVendorData{
                VendorNumber: payabli.String(
                    "7895433",
                ),
            },
        },
    }
client.MoneyOut.AuthorizeOut(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**allowDuplicatedBills:** `*bool` — When `true`, the authorization bypasses the requirement for unique bills, identified by vendor invoice number. This allows you to make more than one payout authorization for a bill, like a split payment.
    
</dd>
</dl>

<dl>
<dd>

**doNotCreateBills:** `*bool` — When `true`, Payabli won't automatically create a bill for this payout transaction.
    
</dd>
</dl>

<dl>
<dd>

**forceVendorCreation:** `*bool` — When `true`, the request creates a new vendor record, regardless of whether the vendor already exists.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.AuthorizePayoutBody` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.CancelAllOut(request) -> *payabli.CaptureAllOutResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancels an array of payout transactions.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := []string{
        "2-29",
        "2-28",
        "2-27",
    }
client.MoneyOut.CancelAllOut(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `[]string` — Array of identifiers of payout transactions to cancel.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.CancelOutGet(ReferenceId) -> *payabli.PayabliApiResponse0000</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a payout transaction by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyOut.CancelOutGet(
        context.TODO(),
        "129-219",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**referenceId:** `string` — The ID for the payout transaction. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.CancelOutDelete(ReferenceId) -> *payabli.PayabliApiResponse0000</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a payout transaction by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyOut.CancelOutDelete(
        context.TODO(),
        "129-219",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**referenceId:** `string` — The ID for the payout transaction. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.CaptureAllOut(request) -> *payabli.CaptureAllOutResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Captures an array of authorized payout transactions for settlement. The maximum number of transactions that can be captured in a single request is 500.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.CaptureAllOutRequest{
        Body: []string{
            "2-29",
            "2-28",
            "2-27",
        },
    }
client.MoneyOut.CaptureAllOut(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `[]string` — Array of identifiers of payout transactions to capture.  
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.CaptureOut(ReferenceId) -> *payabli.AuthCapturePayoutResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Captures a single authorized payout transaction by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.CaptureOutRequest{}
client.MoneyOut.CaptureOut(
        context.TODO(),
        "129-219",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**referenceId:** `string` — The ID for the payout transaction. 
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.PayoutDetails(TransId) -> *payabli.BillDetailResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns details for a processed money out transaction.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyOut.PayoutDetails(
        context.TODO(),
        "45-as456777hhhhhhhhhh77777777-324",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — ReferenceId for the transaction (PaymentId).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.VCardGet(CardToken) -> *payabli.VCardGetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves vCard details for a single card in an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyOut.VCardGet(
        context.TODO(),
        "20230403315245421165",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**cardToken:** `string` — ID for a virtual card.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.SendVCardLink(request) -> *payabli.OperationResult</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Sends a virtual card link via email to the vendor associated with the `transId`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.SendVCardLinkRequest{
        TransId: "01K33Z6YQZ6GD5QVKZ856MJBSC",
    }
client.MoneyOut.SendVCardLink(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**transId:** `string` — The transaction ID of the virtual card payout. The ID is returned as `ReferenceId` in the response when you authorize a payout with POST /MoneyOut/authorize.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.MoneyOut.GetCheckImage(AssetName) -> string</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve the image of a check associated with a processed transaction. 
The check image is returned in the response body as a base64-encoded string. 
The check image is only available for payouts that have been processed.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.MoneyOut.GetCheckImage(
        context.TODO(),
        "check133832686289732320_01JKBNZ5P32JPTZY8XXXX000000.pdf",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**assetName:** `string` 

Name of the check asset to retrieve. This is returned as `filename` in the `CheckData` object 
in the response when you make a GET request to `/MoneyOut/details/{transId}`.
```
    "CheckData": {
      "ftype": "PDF",
      "filename": "check133832686289732320_01JKBNZ5P32JPTZY8XXXX000000.pdf",
      "furl": "",
      "fContent": ""
  }
```
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Notification
<details><summary><code>client.Notification.AddNotification(request) -> *payabli.PayabliApiResponseNotifications</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a new notification or autogenerated report. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddNotificationRequest{
        NotificationStandardRequest: &payabli.NotificationStandardRequest{
            Content: &payabli.NotificationStandardRequestContent{
                EventType: payabli.NotificationStandardRequestContentEventTypeCreatedApplication.Ptr(),
            },
            Frequency: payabli.NotificationStandardRequestFrequencyUntilcancelled,
            Method: payabli.NotificationStandardRequestMethodWeb,
            OwnerId: payabli.String(
                "236",
            ),
            OwnerType: 0,
            Status: payabli.Int(
                1,
            ),
            Target: "https://webhook.site/2871b8f8-edc7-441a-b376-98d8c8e33275",
        },
    }
client.Notification.AddNotification(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*payabli.AddNotificationRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Notification.DeleteNotification(NId) -> *payabli.PayabliApiResponseNotifications</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a single notification or autogenerated report.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Notification.DeleteNotification(
        context.TODO(),
        "1717",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**nId:** `string` — Notification ID. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Notification.GetNotification(NId) -> *payabli.NotificationQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a single notification or autogenerated report's details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Notification.GetNotification(
        context.TODO(),
        "1717",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**nId:** `string` — Notification ID. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Notification.UpdateNotification(NId, request) -> *payabli.PayabliApiResponseNotifications</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update a notification or autogenerated report. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.UpdateNotificationRequest{
        NotificationStandardRequest: &payabli.NotificationStandardRequest{
            Content: &payabli.NotificationStandardRequestContent{
                EventType: payabli.NotificationStandardRequestContentEventTypeApprovedPayment.Ptr(),
            },
            Frequency: payabli.NotificationStandardRequestFrequencyUntilcancelled,
            Method: payabli.NotificationStandardRequestMethodEmail,
            OwnerId: payabli.String(
                "136",
            ),
            OwnerType: 0,
            Status: payabli.Int(
                1,
            ),
            Target: "newemail@email.com",
        },
    }
client.Notification.UpdateNotification(
        context.TODO(),
        "1717",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**nId:** `string` — Notification ID. 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.UpdateNotificationRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Notification.GetReportFile(Id) -> payabli.File</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Gets a copy of a generated report by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Notification.GetReportFile(
        context.TODO(),
        1000000,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `int64` — Report ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Notificationlogs
<details><summary><code>client.Notificationlogs.SearchNotificationLogs(request) -> []*payabli.NotificationLog</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search notification logs with filtering and pagination.
  - Start date and end date cannot be more than 30 days apart
  - Either `orgId` or `paypointId` must be provided

This endpoint requires the `notifications_create` OR `notifications_read` permission.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.SearchNotificationLogsRequest{
        PageSize: payabli.Int(
            20,
        ),
        Body: &payabli.NotificationLogSearchRequest{
            StartDate: payabli.MustParseDateTime(
                "2024-01-01T00:00:00Z",
            ),
            EndDate: payabli.MustParseDateTime(
                "2024-01-31T23:59:59Z",
            ),
            OrgId: payabli.Int64(
                12345,
            ),
            NotificationEvent: payabli.String(
                "ActivatedMerchant",
            ),
            Succeeded: payabli.Bool(
                true,
            ),
        },
    }
client.Notificationlogs.SearchNotificationLogs(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**pageSize:** `*payabli.Pagesize` 
    
</dd>
</dl>

<dl>
<dd>

**page:** `*int` — The page number to retrieve. Defaults to 1 if not provided.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.NotificationLogSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Notificationlogs.GetNotificationLog(Uuid) -> *payabli.NotificationLogDetail</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get detailed information for a specific notification log entry.
This endpoint requires the `notifications_create` OR `notifications_read` permission.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Notificationlogs.GetNotificationLog(
        context.TODO(),
        uuid.MustParse(
            "550e8400-e29b-41d4-a716-446655440000",
        ),
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**uuid:** `uuid.UUID` — The notification log entry.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Notificationlogs.RetryNotificationLog(Uuid) -> *payabli.NotificationLogDetail</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retry sending a specific notification.

**Permissions:** notifications_create
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Notificationlogs.RetryNotificationLog(
        context.TODO(),
        uuid.MustParse(
            "550e8400-e29b-41d4-a716-446655440000",
        ),
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**uuid:** `uuid.UUID` — Unique id
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Notificationlogs.BulkRetryNotificationLogs(request) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retry sending multiple notifications (maximum 50 IDs).
This is an async process, so use the search endpoint again to check the notification status.

This endpoint requires the `notifications_create` permission.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := []uuid.UUID{
        uuid.MustParse(
            "550e8400-e29b-41d4-a716-446655440000",
        ),
        uuid.MustParse(
            "550e8400-e29b-41d4-a716-446655440001",
        ),
        uuid.MustParse(
            "550e8400-e29b-41d4-a716-446655440002",
        ),
    }
client.Notificationlogs.BulkRetryNotificationLogs(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `payabli.BulkRetryRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Ocr
<details><summary><code>client.Ocr.OcrDocumentForm(TypeResult, request) -> *payabli.PayabliApiResponseOcr</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to upload an image file for OCR processing. The accepted file formats include PDF, JPG, JPEG, PNG, and GIF. Specify the desired type of result (either 'bill' or 'invoice') in the path parameter `typeResult`. The response will contain the OCR processing results, including extracted data such as bill number, vendor information, bill items, and more.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.FileContentImageOnly{}
client.Ocr.OcrDocumentForm(
        context.TODO(),
        "typeResult",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**typeResult:** `payabli.TypeResult` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.FileContentImageOnly` — The image file to OCR. Accepted formats include PDF, JPG, JPEG, PNG, GIF.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Ocr.OcrDocumentJson(TypeResult, request) -> *payabli.PayabliApiResponseOcr</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to submit a Base64-encoded image file for OCR processing. The accepted file formats include PDF, JPG, JPEG, PNG, and GIF. Specify the desired type of result (either 'bill' or 'invoice') in the path parameter `typeResult`. The response will contain the OCR processing results, including extracted data such as bill number, vendor information, bill items, and more.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.FileContentImageOnly{}
client.Ocr.OcrDocumentJson(
        context.TODO(),
        "typeResult",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**typeResult:** `payabli.TypeResult` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.FileContentImageOnly` — Base64-encoded file content for OCR processing
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Organization
<details><summary><code>client.Organization.AddOrganization(request) -> *payabli.AddOrganizationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates an organization under a parent organization. This is also referred to as a suborganization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddOrganizationRequest{
        IdempotencyKey: payabli.String(
            "6B29FC40-CA47-1067-B31D-00DD010662DA",
        ),
        BillingInfo: &payabli.Instrument{
            AchAccount: "123123123",
            AchRouting: "123123123",
            BillingAddress: payabli.String(
                "123 Walnut Street",
            ),
            BillingCity: payabli.String(
                "Johnson City",
            ),
            BillingCountry: payabli.String(
                "US",
            ),
            BillingState: payabli.String(
                "TN",
            ),
            BillingZip: payabli.String(
                "37615",
            ),
        },
        Contacts: []*payabli.Contacts{
            &payabli.Contacts{
                ContactEmail: payabli.String(
                    "herman@hermanscoatings.com",
                ),
                ContactName: payabli.String(
                    "Herman Martinez",
                ),
                ContactPhone: payabli.String(
                    "3055550000",
                ),
                ContactTitle: payabli.String(
                    "Owner",
                ),
            },
        },
        HasBilling: payabli.Bool(
            true,
        ),
        HasResidual: payabli.Bool(
            true,
        ),
        OrgAddress: payabli.String(
            "123 Walnut Street",
        ),
        OrgCity: payabli.String(
            "Johnson City",
        ),
        OrgCountry: payabli.String(
            "US",
        ),
        OrgEntryName: payabli.String(
            "pilgrim-planner",
        ),
        OrgId: payabli.String(
            "123",
        ),
        OrgLogo: &payabli.FileContent{
            FContent: payabli.String(
                "TXkgdGVzdCBmaWxlHJ==...",
            ),
            Filename: payabli.String(
                "my-doc.pdf",
            ),
            Ftype: payabli.FileContentFtypePdf.Ptr(),
            Furl: payabli.String(
                "https://mysite.com/my-doc.pdf",
            ),
        },
        OrgName: "Pilgrim Planner",
        OrgParentId: payabli.Int64(
            236,
        ),
        OrgState: payabli.String(
            "TN",
        ),
        OrgTimezone: payabli.Int(
            -5,
        ),
        OrgType: 0,
        OrgWebsite: payabli.String(
            "www.pilgrimageplanner.com",
        ),
        OrgZip: payabli.String(
            "37615",
        ),
        ReplyToEmail: "email@example.com",
    }
client.Organization.AddOrganization(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**services:** `[]*payabli.ServiceCost` 
    
</dd>
</dl>

<dl>
<dd>

**billingInfo:** `*payabli.Instrument` 
    
</dd>
</dl>

<dl>
<dd>

**contacts:** `*payabli.ContactsField` 
    
</dd>
</dl>

<dl>
<dd>

**hasBilling:** `*bool` 
    
</dd>
</dl>

<dl>
<dd>

**hasResidual:** `*bool` 
    
</dd>
</dl>

<dl>
<dd>

**orgAddress:** `*payabli.Orgaddress` 
    
</dd>
</dl>

<dl>
<dd>

**orgCity:** `*payabli.Orgcity` 
    
</dd>
</dl>

<dl>
<dd>

**orgCountry:** `*payabli.Orgcountry` 
    
</dd>
</dl>

<dl>
<dd>

**orgEntryName:** `*payabli.Orgentryname` 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `*payabli.Orgidstring` 
    
</dd>
</dl>

<dl>
<dd>

**orgLogo:** `*payabli.FileContent` 
    
</dd>
</dl>

<dl>
<dd>

**orgName:** `payabli.Orgname` 
    
</dd>
</dl>

<dl>
<dd>

**orgParentId:** `*payabli.OrgParentId` 
    
</dd>
</dl>

<dl>
<dd>

**orgState:** `*payabli.Orgstate` 
    
</dd>
</dl>

<dl>
<dd>

**orgTimezone:** `*payabli.Orgtimezone` 
    
</dd>
</dl>

<dl>
<dd>

**orgType:** `payabli.Orgtype` 
    
</dd>
</dl>

<dl>
<dd>

**orgWebsite:** `*payabli.Orgwebsite` 
    
</dd>
</dl>

<dl>
<dd>

**orgZip:** `*payabli.Orgzip` 
    
</dd>
</dl>

<dl>
<dd>

**replyToEmail:** `payabli.ReplyToEmail` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organization.DeleteOrganization(OrgId) -> *payabli.DeleteOrganizationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete an organization by ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Organization.DeleteOrganization(
        context.TODO(),
        123,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organization.EditOrganization(OrgId, request) -> *payabli.EditOrganizationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates an organization's details by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.OrganizationData{
        Contacts: []*payabli.Contacts{
            &payabli.Contacts{
                ContactEmail: payabli.String(
                    "herman@hermanscoatings.com",
                ),
                ContactName: payabli.String(
                    "Herman Martinez",
                ),
                ContactPhone: payabli.String(
                    "3055550000",
                ),
                ContactTitle: payabli.String(
                    "Owner",
                ),
            },
        },
        OrgAddress: payabli.String(
            "123 Walnut Street",
        ),
        OrgCity: payabli.String(
            "Johnson City",
        ),
        OrgCountry: payabli.String(
            "US",
        ),
        OrgEntryName: payabli.String(
            "pilgrim-planner",
        ),
        OrganizationDataOrgId: payabli.String(
            "123",
        ),
        OrgName: payabli.String(
            "Pilgrim Planner",
        ),
        OrgState: payabli.String(
            "TN",
        ),
        OrgTimezone: payabli.Int(
            -5,
        ),
        OrgType: payabli.Int(
            0,
        ),
        OrgWebsite: payabli.String(
            "www.pilgrimageplanner.com",
        ),
        OrgZip: payabli.String(
            "37615",
        ),
    }
client.Organization.EditOrganization(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**services:** `[]*payabli.ServiceCost` 
    
</dd>
</dl>

<dl>
<dd>

**billingInfo:** `*payabli.Instrument` 
    
</dd>
</dl>

<dl>
<dd>

**contacts:** `*payabli.ContactsField` 
    
</dd>
</dl>

<dl>
<dd>

**hasBilling:** `*bool` 
    
</dd>
</dl>

<dl>
<dd>

**hasResidual:** `*bool` 
    
</dd>
</dl>

<dl>
<dd>

**orgAddress:** `*payabli.Orgaddress` 
    
</dd>
</dl>

<dl>
<dd>

**orgCity:** `*payabli.Orgcity` 
    
</dd>
</dl>

<dl>
<dd>

**orgCountry:** `*payabli.Orgcountry` 
    
</dd>
</dl>

<dl>
<dd>

**orgEntryName:** `*payabli.Orgentryname` 
    
</dd>
</dl>

<dl>
<dd>

**organizationDataOrgId:** `*payabli.Orgidstring` 
    
</dd>
</dl>

<dl>
<dd>

**orgLogo:** `*payabli.FileContent` 
    
</dd>
</dl>

<dl>
<dd>

**orgName:** `*payabli.Orgname` 
    
</dd>
</dl>

<dl>
<dd>

**orgParentId:** `*payabli.OrgParentId` 
    
</dd>
</dl>

<dl>
<dd>

**orgState:** `*payabli.Orgstate` 
    
</dd>
</dl>

<dl>
<dd>

**orgTimezone:** `*payabli.Orgtimezone` 
    
</dd>
</dl>

<dl>
<dd>

**orgType:** `*payabli.Orgtype` 
    
</dd>
</dl>

<dl>
<dd>

**orgWebsite:** `*payabli.Orgwebsite` 
    
</dd>
</dl>

<dl>
<dd>

**orgZip:** `*payabli.Orgzip` 
    
</dd>
</dl>

<dl>
<dd>

**replyToEmail:** `*payabli.ReplyToEmail` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organization.GetBasicOrganization(Entry) -> *payabli.OrganizationQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Gets an organization's basic information by entry name (entrypoint identifier).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Organization.GetBasicOrganization(
        context.TODO(),
        "8cfec329267",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organization.GetBasicOrganizationById(OrgId) -> *payabli.OrganizationQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Gets an organizations basic details by org ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Organization.GetBasicOrganizationById(
        context.TODO(),
        123,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organization.GetOrganization(OrgId) -> *payabli.OrganizationQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves details for an organization by ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Organization.GetOrganization(
        context.TODO(),
        123,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organization.GetSettingsOrganization(OrgId) -> *payabli.SettingsQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves an organization's settings.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Organization.GetSettingsOrganization(
        context.TODO(),
        123,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## PaymentLink
<details><summary><code>client.PaymentLink.AddPayLinkFromInvoice(IdInvoice, request) -> *payabli.PayabliApiResponsePaymentLinks</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Generates a payment link for an invoice from the invoice ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.PayLinkDataInvoice{
        Mail2: payabli.String(
            "jo@example.com; ceo@example.com",
        ),
        Body: &payabli.PaymentPageRequestBody{
            ContactUs: &payabli.ContactElement{
                EmailLabel: payabli.String(
                    "Email",
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Contact Us",
                ),
                Order: payabli.Int(
                    0,
                ),
                PaymentIcons: payabli.Bool(
                    true,
                ),
                PhoneLabel: payabli.String(
                    "Phone",
                ),
            },
            Invoices: &payabli.InvoiceElement{
                Enabled: payabli.Bool(
                    true,
                ),
                InvoiceLink: &payabli.LabelElement{
                    Enabled: payabli.Bool(
                        true,
                    ),
                    Label: payabli.String(
                        "View Invoice",
                    ),
                    Order: payabli.Int(
                        0,
                    ),
                },
                Order: payabli.Int(
                    0,
                ),
                ViewInvoiceDetails: &payabli.LabelElement{
                    Enabled: payabli.Bool(
                        true,
                    ),
                    Label: payabli.String(
                        "Invoice Details",
                    ),
                    Order: payabli.Int(
                        0,
                    ),
                },
            },
            Logo: &payabli.Element{
                Enabled: payabli.Bool(
                    true,
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            MessageBeforePaying: &payabli.LabelElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Label: payabli.String(
                    "Please review your payment details",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Notes: &payabli.NoteElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Additional Notes",
                ),
                Order: payabli.Int(
                    0,
                ),
                Placeholder: payabli.String(
                    "Enter any additional notes here",
                ),
                Value: payabli.String(
                    "",
                ),
            },
            Page: &payabli.PageElement{
                Description: payabli.String(
                    "Complete your payment securely",
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Payment Page",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            PaymentButton: &payabli.LabelElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Label: payabli.String(
                    "Pay Now",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            PaymentMethods: &payabli.MethodElement{
                AllMethodsChecked: payabli.Bool(
                    true,
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Payment Methods",
                ),
                Methods: &payabli.MethodsList{
                    Amex: payabli.Bool(
                        true,
                    ),
                    ApplePay: payabli.Bool(
                        true,
                    ),
                    Discover: payabli.Bool(
                        true,
                    ),
                    ECheck: payabli.Bool(
                        true,
                    ),
                    Mastercard: payabli.Bool(
                        true,
                    ),
                    Visa: payabli.Bool(
                        true,
                    ),
                },
                Order: payabli.Int(
                    0,
                ),
                Settings: &payabli.MethodElementSettings{
                    ApplePay: &payabli.MethodElementSettingsApplePay{
                        ButtonStyle: payabli.MethodElementSettingsApplePayButtonStyleBlack.Ptr(),
                        ButtonType: payabli.MethodElementSettingsApplePayButtonTypePay.Ptr(),
                        Language: payabli.MethodElementSettingsApplePayLanguageEnUs.Ptr(),
                    },
                },
            },
            Payor: &payabli.PayorElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Fields: []*payabli.PayorFields{
                    &payabli.PayorFields{
                        Display: payabli.Bool(
                            true,
                        ),
                        Fixed: payabli.Bool(
                            true,
                        ),
                        Identifier: payabli.Bool(
                            true,
                        ),
                        Label: payabli.String(
                            "Full Name",
                        ),
                        Name: payabli.String(
                            "fullName",
                        ),
                        Order: payabli.Int(
                            0,
                        ),
                        Required: payabli.Bool(
                            true,
                        ),
                        Validation: payabli.String(
                            "alpha",
                        ),
                        Value: payabli.String(
                            "",
                        ),
                        Width: payabli.Int(
                            0,
                        ),
                    },
                },
                Header: payabli.String(
                    "Payor Information",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Review: &payabli.HeaderElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Review Payment",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Settings: &payabli.PagelinkSetting{
                Color: payabli.String(
                    "#000000",
                ),
                CustomCssUrl: payabli.String(
                    "https://example.com/custom.css",
                ),
                Language: payabli.String(
                    "en",
                ),
                PageLogo: &payabli.FileContent{
                    FContent: payabli.String(
                        "PHN2ZyB2aWV3Qm94PSIwIDAgODAwIDEwMDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CiAgPCEtLSBCYWNrZ3JvdW5kIC0tPgogIDxyZWN0IHdpZHRoPSI4MDAiIGhlaWdodD0iMTAwMCIgZmlsbD0id2hpdGUiLz4KICAKICA8IS0tIENvbXBhbnkgSGVhZGVyIC0tPgogIDx0ZXh0IHg9IjQwIiB5PSI2MCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjI0IiBmb250LXdlaWdodD0iYm9sZCIgZmlsbD0iIzJjM2U1MCI+R3J1enlhIEFkdmVudHVyZSBPdXRmaXR0ZXJzPC90ZXh0PgogIDxsaW5lIHgxPSI0MCIgeTE9IjgwIiB4Mj0iNzYwIiB5Mj0iODAiIHN0cm9rZT0iIzJjM2U1MCIgc3Ryb2tlLXdpZHRoPSIyIi8+CiAgCiAgPCEtLSBDb21wYW55IERldGFpbHMgLS0+CiAgPHRleHQgeD0iNDAiIHk9IjExMCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmaWxsPSIjMzQ0OTVlIj4xMjMgTW91bnRhaW4gVmlldyBSb2FkPC90ZXh0PgogIDx0ZXh0IHg9IjQwIiB5PSIxMzAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+VGJpbGlzaSwgR2VvcmdpYSAwMTA1PC90ZXh0PgogIDx0ZXh0IHg9IjQwIiB5PSIxNTAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+VGVsOiArOTk1IDMyIDEyMyA0NTY3PC90ZXh0PgogIDx0ZXh0IHg9IjQwIiB5PSIxNzAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+RW1haWw6IGluZm9AZ3J1enlhYWR2ZW50dXJlcy5jb208L3RleHQ+CgogIDwhLS0gSW52b2ljZSBUaXRsZSAtLT4KICA8dGV4dCB4PSI2MDAiIHk9IjExMCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjI0IiBmb250LXdlaWdodD0iYm9sZCIgZmlsbD0iIzJjM2U1MCI+SU5WT0lDRTwvdGV4dD4KICA8dGV4dCB4PSI2MDAiIHk9IjE0MCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmaWxsPSIjMzQ0OTVlIj5EYXRlOiAxMi8xMS8yMDI0PC90ZXh0PgogIDx0ZXh0IHg9IjYwMCIgeT0iMTYwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPkludm9pY2UgIzogR1JaLTIwMjQtMTEyMzwvdGV4dD4KCiAgPCEtLSBCaWxsIFRvIFNlY3Rpb24gLS0+CiAgPHRleHQgeD0iNDAiIHk9IjIyMCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE2IiBmb250LXdlaWdodD0iYm9sZCIgZmlsbD0iIzJjM2U1MCI+QklMTCBUTzo8L3RleHQ+CiAgPHJlY3QgeD0iNDAiIHk9IjIzNSIgd2lkdGg9IjMwMCIgaGVpZ2h0PSI4MCIgZmlsbD0iI2Y3ZjlmYSIvPgogIDx0ZXh0IHg9IjUwIiB5PSIyNjAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+W0N1c3RvbWVyIE5hbWVdPC90ZXh0PgogIDx0ZXh0IHg9IjUwIiB5PSIyODAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+W0FkZHJlc3MgTGluZSAxXTwvdGV4dD4KICA8dGV4dCB4PSI1MCIgeT0iMzAwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPltDaXR5LCBDb3VudHJ5XTwvdGV4dD4KCiAgPCEtLSBUYWJsZSBIZWFkZXJzIC0tPgogIDxyZWN0IHg9IjQwIiB5PSIzNDAiIHdpZHRoPSI3MjAiIGhlaWdodD0iMzAiIGZpbGw9IiMyYzNlNTAiLz4KICA8dGV4dCB4PSI1MCIgeT0iMzYwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZvbnQtd2VpZ2h0PSJib2xkIiBmaWxsPSJ3aGl0ZSI+RGVzY3JpcHRpb248L3RleHQ+CiAgPHRleHQgeD0iNDUwIiB5PSIzNjAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZm9udC13ZWlnaHQ9ImJvbGQiIGZpbGw9IndoaXRlIj5RdWFudGl0eTwvdGV4dD4KICA8dGV4dCB4PSI1NTAiIHk9IjM2MCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmb250LXdlaWdodD0iYm9sZCIgZmlsbD0id2hpdGUiPlJhdGU8L3RleHQ+CiAgPHRleHQgeD0iNjgwIiB5PSIzNjAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZm9udC13ZWlnaHQ9ImJvbGQiIGZpbGw9IndoaXRlIj5BbW91bnQ8L3RleHQ+CgogIDwhLS0gVGFibGUgUm93cyAtLT4KICA8cmVjdCB4PSI0MCIgeT0iMzcwIiB3aWR0aD0iNzIwIiBoZWlnaHQ9IjMwIiBmaWxsPSIjZjdmOWZhIi8+CiAgPHRleHQgeD0iNTAiIHk9IjM5MCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmaWxsPSIjMzQ0OTVlIj5Nb3VudGFpbiBDbGltYmluZyBFcXVpcG1lbnQgUmVudGFsPC90ZXh0PgogIDx0ZXh0IHg9IjQ1MCIgeT0iMzkwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPjE8L3RleHQ+CiAgPHRleHQgeD0iNTUwIiB5PSIzOTAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+JDI1MC4wMDwvdGV4dD4KICA8dGV4dCB4PSI2ODAiIHk9IjM5MCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmaWxsPSIjMzQ0OTVlIj4kMjUwLjAwPC90ZXh0PgoKICA8cmVjdCB4PSI0MCIgeT0iNDAwIiB3aWR0aD0iNzIwIiBoZWlnaHQ9IjMwIiBmaWxsPSJ3aGl0ZSIvPgogIDx0ZXh0IHg9IjUwIiB5PSI0MjAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+R3VpZGVkIFRyZWsgUGFja2FnZSAtIDIgRGF5czwvdGV4dD4KICA8dGV4dCB4PSI0NTAiIHk9IjQyMCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmaWxsPSIjMzQ0OTVlIj4xPC90ZXh0PgogIDx0ZXh0IHg9IjU1MCIgeT0iNDIwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPiQ0MDAuMDA8L3RleHQ+CiAgPHRleHQgeD0iNjgwIiB5PSI0MjAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+JDQwMC4wMDwvdGV4dD4KCiAgPHJlY3QgeD0iNDAiIHk9IjQzMCIgd2lkdGg9IjcyMCIgaGVpZ2h0PSIzMCIgZmlsbD0iI2Y3ZjlmYSIvPgogIDx0ZXh0IHg9IjUwIiB5PSI0NTAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+U2FmZXR5IEVxdWlwbWVudCBQYWNrYWdlPC90ZXh0PgogIDx0ZXh0IHg9IjQ1MCIgeT0iNDUwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPjE8L3RleHQ+CiAgPHRleHQgeD0iNTUwIiB5PSI0NTAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+JDE1MC4wMDwvdGV4dD4KICA8dGV4dCB4PSI2ODAiIHk9IjQ1MCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmaWxsPSIjMzQ0OTVlIj4kMTUwLjAwPC90ZXh0PgoKICA8IS0tIFRvdGFscyAtLT4KICA8bGluZSB4MT0iNDAiIHkxPSI0ODAiIHgyPSI3NjAiIHkyPSI0ODAiIHN0cm9rZT0iIzJjM2U1MCIgc3Ryb2tlLXdpZHRoPSIxIi8+CiAgPHRleHQgeD0iNTUwIiB5PSI1MTAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZm9udC13ZWlnaHQ9ImJvbGQiIGZpbGw9IiMzNDQ5NWUiPlN1YnRvdGFsOjwvdGV4dD4KICA8dGV4dCB4PSI2ODAiIHk9IjUxMCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmaWxsPSIjMzQ0OTVlIj4kODAwLjAwPC90ZXh0PgogIDx0ZXh0IHg9IjU1MCIgeT0iNTM1IiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZvbnQtd2VpZ2h0PSJib2xkIiBmaWxsPSIjMzQ0OTVlIj5UYXggKDE4JSk6PC90ZXh0PgogIDx0ZXh0IHg9IjY4MCIgeT0iNTM1IiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPiQxNDQuMDA8L3RleHQ+CiAgPHRleHQgeD0iNTUwIiB5PSI1NzAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNiIgZm9udC13ZWlnaHQ9ImJvbGQiIGZpbGw9IiMyYzNlNTAiPlRvdGFsOjwvdGV4dD4KICA8dGV4dCB4PSI2ODAiIHk9IjU3MCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE2IiBmb250LXdlaWdodD0iYm9sZCIgZmlsbD0iIzJjM2U1MCI+JDk0NC4wMDwvdGV4dD4KCiAgPCEtLSBQYXltZW50IFRlcm1zIC0tPgogIDx0ZXh0IHg9IjQwIiB5PSI2NDAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNiIgZm9udC13ZWlnaHQ9ImJvbGQiIGZpbGw9IiMyYzNlNTAiPlBheW1lbnQgVGVybXM8L3RleHQ+CiAgPHRleHQgeD0iNDAiIHk9IjY3MCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjE0IiBmaWxsPSIjMzQ0OTVlIj5QYXltZW50IGlzIGR1ZSB3aXRoaW4gMzAgZGF5czwvdGV4dD4KICA8dGV4dCB4PSI0MCIgeT0iNjkwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPlBsZWFzZSBpbmNsdWRlIGludm9pY2UgbnVtYmVyIG9uIHBheW1lbnQ8L3RleHQ+CgogIDwhLS0gQmFuayBEZXRhaWxzIC0tPgogIDx0ZXh0IHg9IjQwIiB5PSI3MzAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNiIgZm9udC13ZWlnaHQ9ImJvbGQiIGZpbGw9IiMyYzNlNTAiPkJhbmsgRGV0YWlsczwvdGV4dD4KICA8dGV4dCB4PSI0MCIgeT0iNzYwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPkJhbms6IEJhbmsgb2YgR2VvcmdpYTwvdGV4dD4KICA8dGV4dCB4PSI0MCIgeT0iNzgwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTQiIGZpbGw9IiMzNDQ5NWUiPklCQU46IEdFMTIzNDU2Nzg5MDEyMzQ1Njc4PC90ZXh0PgogIDx0ZXh0IHg9IjQwIiB5PSI4MDAiIGZvbnQtZmFtaWx5PSJBcmlhbCIgZm9udC1zaXplPSIxNCIgZmlsbD0iIzM0NDk1ZSI+U1dJRlQ6IEJBR0FHRTIyPC90ZXh0PgoKICA8IS0tIEZvb3RlciAtLT4KICA8bGluZSB4MT0iNDAiIHkxPSI5MDAiIHgyPSI3NjAiIHkyPSI5MDAiIHN0cm9rZT0iIzJjM2U1MCIgc3Ryb2tlLXdpZHRoPSIxIi8+CiAgPHRleHQgeD0iNDAiIHk9IjkzMCIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiBmaWxsPSIjN2Y4YzhkIj5UaGFuayB5b3UgZm9yIGNob29zaW5nIEdydXp5YSBBZHZlbnR1cmUgT3V0Zml0dGVyczwvdGV4dD4KICA8dGV4dCB4PSI0MCIgeT0iOTUwIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTIiIGZpbGw9IiM3ZjhjOGQiPnd3dy5ncnV6eWFhZHZlbnR1cmVzLmNvbTwvdGV4dD4KPC9zdmc+Cg==",
                    ),
                    Filename: payabli.String(
                        "logo.jpg",
                    ),
                    Ftype: payabli.FileContentFtypeJpg.Ptr(),
                    Furl: payabli.String(
                        "",
                    ),
                },
                RedirectAfterApprove: payabli.Bool(
                    true,
                ),
                RedirectAfterApproveUrl: payabli.String(
                    "https://example.com/success",
                ),
            },
        },
    }
client.PaymentLink.AddPayLinkFromInvoice(
        context.TODO(),
        23548884,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idInvoice:** `int` — Invoice ID
    
</dd>
</dl>

<dl>
<dd>

**amountFixed:** `*bool` — Indicates whether customer can modify the payment amount. A value of `true` means the amount isn't modifiable, a value `false` means the payor can modify the amount to pay.
    
</dd>
</dl>

<dl>
<dd>

**mail2:** `*string` — List of recipient email addresses. When there is more than one, separate them by a semicolon (;).
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.PaymentPageRequestBody` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentLink.AddPayLinkFromBill(BillId, request) -> *payabli.PayabliApiResponsePaymentLinks</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Generates a payment link for a bill from the bill ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.PayLinkDataBill{
        Mail2: payabli.String(
            "jo@example.com; ceo@example.com",
        ),
        Body: &payabli.PaymentPageRequestBody{
            ContactUs: &payabli.ContactElement{
                EmailLabel: payabli.String(
                    "Email",
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Contact Us",
                ),
                Order: payabli.Int(
                    0,
                ),
                PaymentIcons: payabli.Bool(
                    true,
                ),
                PhoneLabel: payabli.String(
                    "Phone",
                ),
            },
            Logo: &payabli.Element{
                Enabled: payabli.Bool(
                    true,
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            MessageBeforePaying: &payabli.LabelElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Label: payabli.String(
                    "Please review your payment details",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Notes: &payabli.NoteElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Additional Notes",
                ),
                Order: payabli.Int(
                    0,
                ),
                Placeholder: payabli.String(
                    "Enter any additional notes here",
                ),
                Value: payabli.String(
                    "",
                ),
            },
            Page: &payabli.PageElement{
                Description: payabli.String(
                    "Get paid securely",
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Payment Page",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            PaymentButton: &payabli.LabelElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Label: payabli.String(
                    "Pay Now",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            PaymentMethods: &payabli.MethodElement{
                AllMethodsChecked: payabli.Bool(
                    true,
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Payment Methods",
                ),
                Methods: &payabli.MethodsList{
                    Amex: payabli.Bool(
                        true,
                    ),
                    ApplePay: payabli.Bool(
                        true,
                    ),
                    Discover: payabli.Bool(
                        true,
                    ),
                    ECheck: payabli.Bool(
                        true,
                    ),
                    Mastercard: payabli.Bool(
                        true,
                    ),
                    Visa: payabli.Bool(
                        true,
                    ),
                },
                Order: payabli.Int(
                    0,
                ),
            },
            Payor: &payabli.PayorElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Fields: []*payabli.PayorFields{
                    &payabli.PayorFields{
                        Display: payabli.Bool(
                            true,
                        ),
                        Fixed: payabli.Bool(
                            true,
                        ),
                        Identifier: payabli.Bool(
                            true,
                        ),
                        Label: payabli.String(
                            "Full Name",
                        ),
                        Name: payabli.String(
                            "fullName",
                        ),
                        Order: payabli.Int(
                            0,
                        ),
                        Required: payabli.Bool(
                            true,
                        ),
                        Validation: payabli.String(
                            "alpha",
                        ),
                        Value: payabli.String(
                            "",
                        ),
                        Width: payabli.Int(
                            0,
                        ),
                    },
                },
                Header: payabli.String(
                    "Payor Information",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Review: &payabli.HeaderElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Review Payment",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Settings: &payabli.PagelinkSetting{
                Color: payabli.String(
                    "#000000",
                ),
                Language: payabli.String(
                    "en",
                ),
            },
        },
    }
client.PaymentLink.AddPayLinkFromBill(
        context.TODO(),
        23548884,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**billId:** `int` — The Payabli ID for the bill.
    
</dd>
</dl>

<dl>
<dd>

**amountFixed:** `*bool` — Indicates whether customer can modify the payment amount. A value of `true` means the amount isn't modifiable, a value `false` means the payor can modify the amount to pay.
    
</dd>
</dl>

<dl>
<dd>

**mail2:** `*string` — List of recipient email addresses. When there is more than one, separate them by a semicolon (;).
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.PaymentPageRequestBody` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentLink.DeletePayLinkFromId(PayLinkId) -> *payabli.PayabliApiResponsePaymentLinks</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a payment link by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.PaymentLink.DeletePayLinkFromId(
        context.TODO(),
        "payLinkId",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**payLinkId:** `string` — ID for the payment link.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentLink.GetPayLinkFromId(PaylinkId) -> *payabli.GetPayLinkFromIdResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a payment link by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.PaymentLink.GetPayLinkFromId(
        context.TODO(),
        "paylinkId",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**paylinkId:** `string` — ID for payment link
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentLink.PushPayLinkFromId(PayLinkId, request) -> *payabli.PayabliApiResponsePaymentLinks</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Send a payment link to the specified email addresses or phone numbers.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.PushPayLinkRequest{
        Sms: &payabli.PushPayLinkRequestSms{},
    }
client.PaymentLink.PushPayLinkFromId(
        context.TODO(),
        "payLinkId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**payLinkId:** `string` — ID for the payment link.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.PushPayLinkRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentLink.RefreshPayLinkFromId(PayLinkId) -> *payabli.PayabliApiResponsePaymentLinks</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Refresh a payment link's content after an update.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RefreshPayLinkFromIdRequest{}
client.PaymentLink.RefreshPayLinkFromId(
        context.TODO(),
        "payLinkId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**payLinkId:** `string` — ID for the payment link.
    
</dd>
</dl>

<dl>
<dd>

**amountFixed:** `*bool` — Indicates whether customer can modify the payment amount. A value of `true` means the amount isn't modifiable, a value `false` means the payor can modify the amount to pay.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentLink.SendPayLinkFromId(PayLinkId) -> *payabli.PayabliApiResponsePaymentLinks</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Sends a payment link to the specified email addresses. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.SendPayLinkFromIdRequest{
        Mail2: payabli.String(
            "jo@example.com; ceo@example.com",
        ),
    }
client.PaymentLink.SendPayLinkFromId(
        context.TODO(),
        "payLinkId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**payLinkId:** `string` — ID for the payment link.
    
</dd>
</dl>

<dl>
<dd>

**attachfile:** `*bool` — When `true`, attaches a PDF version of invoice to the email.
    
</dd>
</dl>

<dl>
<dd>

**mail2:** `*string` — List of recipient email addresses. When there is more than one, separate them by a semicolon (;).
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentLink.UpdatePayLinkFromId(PayLinkId, request) -> *payabli.PayabliApiResponsePaymentLinks</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates a payment link's details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.PayLinkUpdateData{
        Notes: &payabli.NoteElement{
            Enabled: payabli.Bool(
                true,
            ),
            Header: payabli.String(
                "Additional Notes",
            ),
            Order: payabli.Int(
                0,
            ),
            Placeholder: payabli.String(
                "Enter any additional notes here",
            ),
            Value: payabli.String(
                "",
            ),
        },
        PaymentButton: &payabli.LabelElement{
            Enabled: payabli.Bool(
                true,
            ),
            Label: payabli.String(
                "Pay Now",
            ),
            Order: payabli.Int(
                0,
            ),
        },
    }
client.PaymentLink.UpdatePayLinkFromId(
        context.TODO(),
        "332-c277b704-1301",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**payLinkId:** `string` — ID for the payment link.
    
</dd>
</dl>

<dl>
<dd>

**contactUs:** `*payabli.ContactElement` — ContactUs section of payment link page
    
</dd>
</dl>

<dl>
<dd>

**logo:** `*payabli.Element` — Logo section of payment link page
    
</dd>
</dl>

<dl>
<dd>

**messageBeforePaying:** `*payabli.LabelElement` — Message section of payment link page
    
</dd>
</dl>

<dl>
<dd>

**notes:** `*payabli.NoteElement` — Notes section of payment link page
    
</dd>
</dl>

<dl>
<dd>

**page:** `*payabli.PageElement` — Page header section of payment link page
    
</dd>
</dl>

<dl>
<dd>

**paymentButton:** `*payabli.LabelElement` — Payment button section of payment link page
    
</dd>
</dl>

<dl>
<dd>

**paymentMethods:** `*payabli.MethodElement` — Payment methods section of payment link page
    
</dd>
</dl>

<dl>
<dd>

**review:** `*payabli.HeaderElement` — Review section of payment link page
    
</dd>
</dl>

<dl>
<dd>

**settings:** `*payabli.PagelinkSetting` — Settings section of payment link page
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentLink.AddPayLinkFromBillLotNumber(LotNumber, request) -> *payabli.PayabliApiResponsePaymentLinks</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Generates a vendor payment link for a specific bill lot number. This allows you to pay all bills with the same lot number for a vendor with a single payment link.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.PayLinkDataOut{
        EntryPoint: "billing",
        VendorNumber: "VENDOR-123",
        Mail2: payabli.String(
            "customer@example.com; billing@example.com",
        ),
        AmountFixed: payabli.String(
            "true",
        ),
        Body: &payabli.PaymentPageRequestBody{
            ContactUs: &payabli.ContactElement{
                EmailLabel: payabli.String(
                    "Email",
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Contact Us",
                ),
                Order: payabli.Int(
                    0,
                ),
                PaymentIcons: payabli.Bool(
                    true,
                ),
                PhoneLabel: payabli.String(
                    "Phone",
                ),
            },
            Logo: &payabli.Element{
                Enabled: payabli.Bool(
                    true,
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            MessageBeforePaying: &payabli.LabelElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Label: payabli.String(
                    "Please review your payment details",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Notes: &payabli.NoteElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Additional Notes",
                ),
                Order: payabli.Int(
                    0,
                ),
                Placeholder: payabli.String(
                    "Enter any additional notes here",
                ),
                Value: payabli.String(
                    "",
                ),
            },
            Page: &payabli.PageElement{
                Description: payabli.String(
                    "Get paid securely",
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Payment Page",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            PaymentButton: &payabli.LabelElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Label: payabli.String(
                    "Pay Now",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            PaymentMethods: &payabli.MethodElement{
                AllMethodsChecked: payabli.Bool(
                    true,
                ),
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Payment Methods",
                ),
                Methods: &payabli.MethodsList{
                    Amex: payabli.Bool(
                        true,
                    ),
                    ApplePay: payabli.Bool(
                        true,
                    ),
                    Discover: payabli.Bool(
                        true,
                    ),
                    ECheck: payabli.Bool(
                        true,
                    ),
                    Mastercard: payabli.Bool(
                        true,
                    ),
                    Visa: payabli.Bool(
                        true,
                    ),
                },
                Order: payabli.Int(
                    0,
                ),
            },
            Payor: &payabli.PayorElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Fields: []*payabli.PayorFields{
                    &payabli.PayorFields{
                        Display: payabli.Bool(
                            true,
                        ),
                        Fixed: payabli.Bool(
                            true,
                        ),
                        Identifier: payabli.Bool(
                            true,
                        ),
                        Label: payabli.String(
                            "Full Name",
                        ),
                        Name: payabli.String(
                            "fullName",
                        ),
                        Order: payabli.Int(
                            0,
                        ),
                        Required: payabli.Bool(
                            true,
                        ),
                        Validation: payabli.String(
                            "alpha",
                        ),
                        Value: payabli.String(
                            "",
                        ),
                        Width: payabli.Int(
                            0,
                        ),
                    },
                },
                Header: payabli.String(
                    "Payor Information",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Review: &payabli.HeaderElement{
                Enabled: payabli.Bool(
                    true,
                ),
                Header: payabli.String(
                    "Review Payment",
                ),
                Order: payabli.Int(
                    0,
                ),
            },
            Settings: &payabli.PagelinkSetting{
                Color: payabli.String(
                    "#000000",
                ),
                Language: payabli.String(
                    "en",
                ),
            },
        },
    }
client.PaymentLink.AddPayLinkFromBillLotNumber(
        context.TODO(),
        "LOT-2024-001",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**lotNumber:** `string` — Lot number of the bills to pay. All bills with this lot number will be included.
    
</dd>
</dl>

<dl>
<dd>

**entryPoint:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**vendorNumber:** `string` — The vendor number for the vendor being paid with this payment link.
    
</dd>
</dl>

<dl>
<dd>

**mail2:** `*string` — List of recipient email addresses. When there is more than one, separate them by a semicolon (;).
    
</dd>
</dl>

<dl>
<dd>

**amountFixed:** `*string` — Indicates whether customer can modify the payment amount. A value of `true` means the amount isn't modifiable, a value `false` means the payor can modify the amount to pay.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.PaymentPageRequestBody` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## PaymentMethodDomain
<details><summary><code>client.PaymentMethodDomain.AddPaymentMethodDomain(request) -> *payabli.AddPaymentMethodDomainApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Add a payment method domain to an organization or paypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddPaymentMethodDomainRequest{
        DomainName: payabli.String(
            "checkout.example.com",
        ),
        EntityId: payabli.Int64(
            109,
        ),
        EntityType: payabli.String(
            "paypoint",
        ),
        ApplePay: &payabli.AddPaymentMethodDomainRequestApplePay{
            IsEnabled: payabli.Bool(
                true,
            ),
        },
        GooglePay: &payabli.AddPaymentMethodDomainRequestGooglePay{
            IsEnabled: payabli.Bool(
                true,
            ),
        },
    }
client.PaymentMethodDomain.AddPaymentMethodDomain(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**applePay:** `*payabli.AddPaymentMethodDomainRequestApplePay` — Apple Pay configuration information.
    
</dd>
</dl>

<dl>
<dd>

**googlePay:** `*payabli.AddPaymentMethodDomainRequestGooglePay` — Google Pay configuration information.
    
</dd>
</dl>

<dl>
<dd>

**domainName:** `*payabli.DomainName` 
    
</dd>
</dl>

<dl>
<dd>

**entityId:** `*payabli.EntityId` 
    
</dd>
</dl>

<dl>
<dd>

**entityType:** `*payabli.EntityType` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentMethodDomain.CascadePaymentMethodDomain(DomainId) -> *payabli.PaymentMethodDomainGeneralResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cascades a payment method domain to all child entities. All paypoints and suborganization under this parent will inherit this domain and its settings.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.PaymentMethodDomain.CascadePaymentMethodDomain(
        context.TODO(),
        "pmd_b8237fa45c964d8a9ef27160cd42b8c5",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**domainId:** `string` — The payment method domain's ID in Payabli.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentMethodDomain.DeletePaymentMethodDomain(DomainId) -> *payabli.DeletePaymentMethodDomainResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a payment method domain. You can't delete an inherited domain, you must delete a domain at the organization level.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.PaymentMethodDomain.DeletePaymentMethodDomain(
        context.TODO(),
        "pmd_b8237fa45c964d8a9ef27160cd42b8c5",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**domainId:** `string` — The payment method domain's ID in Payabli.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentMethodDomain.GetPaymentMethodDomain(DomainId) -> *payabli.PaymentMethodDomainApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get the details for a payment method domain.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.PaymentMethodDomain.GetPaymentMethodDomain(
        context.TODO(),
        "pmd_b8237fa45c964d8a9ef27160cd42b8c5",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**domainId:** `string` — The payment method domain's ID in Payabli.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentMethodDomain.ListPaymentMethodDomains() -> *payabli.ListPaymentMethodDomainsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a list of payment method domains that belong to a PSP, organization, or paypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListPaymentMethodDomainsRequest{
        EntityId: payabli.Int64(
            1147,
        ),
        EntityType: payabli.String(
            "paypoint",
        ),
    }
client.PaymentMethodDomain.ListPaymentMethodDomains(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entityId:** `*int64` 

Identifier for the organization or paypoint. 
- For organization, provide the organization ID - For paypoint, provide the paypoint ID
    
</dd>
</dl>

<dl>
<dd>

**entityType:** `*string` 

The type of entity. Valid values: 
  - organization
  - paypoint
  - psp
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — Number of records to skip. Defaults to `0`.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records for query response. Defaults to `20`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentMethodDomain.UpdatePaymentMethodDomain(DomainId, request) -> *payabli.PaymentMethodDomainGeneralResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update a payment method domain's configuration values.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.UpdatePaymentMethodDomainRequest{
        ApplePay: &payabli.UpdatePaymentMethodDomainRequestWallet{
            IsEnabled: payabli.Bool(
                false,
            ),
        },
        GooglePay: &payabli.UpdatePaymentMethodDomainRequestWallet{
            IsEnabled: payabli.Bool(
                false,
            ),
        },
    }
client.PaymentMethodDomain.UpdatePaymentMethodDomain(
        context.TODO(),
        "pmd_b8237fa45c964d8a9ef27160cd42b8c5",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**domainId:** `string` — The payment method domain's ID in Payabli.
    
</dd>
</dl>

<dl>
<dd>

**applePay:** `*payabli.UpdatePaymentMethodDomainRequestWallet` 
    
</dd>
</dl>

<dl>
<dd>

**googlePay:** `*payabli.UpdatePaymentMethodDomainRequestWallet` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.PaymentMethodDomain.VerifyPaymentMethodDomain(DomainId) -> *payabli.PaymentMethodDomainGeneralResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Verify a new payment method domain. If verification is successful, Apple Pay is automatically activated for the domain.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.PaymentMethodDomain.VerifyPaymentMethodDomain(
        context.TODO(),
        "pmd_b8237fa45c964d8a9ef27160cd42b8c5",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**domainId:** `string` — The payment method domain's ID in Payabli.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Paypoint
<details><summary><code>client.Paypoint.GetBasicEntry(Entry) -> *payabli.GetBasicEntryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Gets the basic details for a paypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Paypoint.GetBasicEntry(
        context.TODO(),
        "8cfec329267",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Paypoint.GetBasicEntryById(IdPaypoint) -> *payabli.GetBasicEntryByIdResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves the basic details for a paypoint by ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Paypoint.GetBasicEntryById(
        context.TODO(),
        "198",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idPaypoint:** `string` — Paypoint ID. You can find this value by querying `/api/Query/paypoints/{orgId}`
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Paypoint.GetEntryConfig(Entry) -> *payabli.GetEntryConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Gets the details for a single paypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.GetEntryConfigRequest{}
client.Paypoint.GetEntryConfig(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**entrypages:** `*string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Paypoint.GetPage(Entry, Subdomain) -> *payabli.PayabliPages</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Gets the details for single payment page for a paypoint. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Paypoint.GetPage(
        context.TODO(),
        "8cfec329267",
        "pay-your-fees-1",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**subdomain:** `string` — Payment page identifier. The subdomain value is the last portion of the payment page URL. For example, in`https://paypages-sandbox.payabli.com/513823dc10/pay-your-fees-1`, the subdomain is `pay-your-fees-1`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Paypoint.RemovePage(Entry, Subdomain) -> *payabli.PayabliApiResponseGeneric2Part</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a payment page in a paypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Paypoint.RemovePage(
        context.TODO(),
        "8cfec329267",
        "pay-your-fees-1",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**subdomain:** `string` — Payment page identifier. The subdomain value is the last portion of the payment page URL. For example, in`https://paypages-sandbox.payabli.com/513823dc10/pay-your-fees-1`, the subdomain is `pay-your-fees-1`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Paypoint.SaveLogo(Entry, request) -> *payabli.PayabliApiResponse00Responsedatanonobject</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates a paypoint logo. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.FileContent{}
client.Paypoint.SaveLogo(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.FileContent` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Paypoint.SettingsPage(Entry) -> *payabli.SettingsQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves an paypoint's basic settings like custom fields, identifiers, and invoicing settings.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Paypoint.SettingsPage(
        context.TODO(),
        "8cfec329267",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Paypoint.Migrate(request) -> *payabli.MigratePaypointResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Migrates a paypoint to a new parent organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.PaypointMoveRequest{
        EntryPoint: "473abc123def",
        NewParentOrganizationId: 123,
        NotificationRequest: &payabli.NotificationRequest{
            NotificationUrl: "https://webhook-test.yoursie.com",
            WebHeaderParameters: []*payabli.WebHeaderParameter{
                &payabli.WebHeaderParameter{
                    Key: "testheader",
                    Value: "1234567890",
                },
            },
        },
    }
client.Paypoint.Migrate(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*payabli.PaypointMoveRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Query
<details><summary><code>client.Query.ListBatchDetails(Entry) -> *payabli.QueryBatchesDetailResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of batches and their details, including settled and
unsettled transactions for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBatchDetailsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListBatchDetails(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted:**

- `settlementDate` (gt, ge, lt, le, eq, ne)
- `depositDate` (gt, ge, lt, le, eq, ne)
- `transId`  (ne, eq, ct, nct)
- `gatewayTransId`  (ne, eq, ct, nct)
- `method`   (in, nin, eq, ne)
- `settledAmount`  (gt, ge, lt, le, eq, ne)
- `operation`    (in, nin, eq, ne)
- `source`   (in, nin, eq, ne)
- `batchNumber`  (ct, nct, eq, ne)
- `payaccountLastfour`   (nct, ct)
- `payaccountType`   (ne, eq, in, nin)
- `customerFirstname`   (ct, nct, eq, ne)
- `customerLastname`    (ct, nct, eq, ne)
- `customerName`   (ct, nct)
- `customerId`  (eq, ne)
- `customerNumber`  (ct, nct, eq, ne)
- `customerCompanyname`    (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity`    (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity`    (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId`  (eq) *mandatory when entry=org*
- `isHold` (eq, ne)
- `paypointId`  (ne, eq)
- `paypointLegal`  (ne, eq, ct, nct)
- `paypointDba`  (ne, eq, ct, nct)
- `orgName`  (ne, eq, ct, nct)
- `batchId` (ct, nct, eq, neq)
- `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

**List of comparison accepted:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**List of parameters accepted:**

- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `settledAmount(gt)=20` returns all records with a `settledAmount` greater than 20.00.
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListBatchDetailsOrg(OrgId) -> *payabli.QueryResponseSettlements</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of batches and their details, including settled and unsettled transactions for an organization. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBatchDetailsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListBatchDetailsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted:**

- `settlementDate` (gt, ge, lt, le, eq, ne)
- `depositDate` (gt, ge, lt, le, eq, ne)
- `transId`  (ne, eq, ct, nct)
- `gatewayTransId`  (ne, eq, ct, nct)
- `method`   (in, nin, eq, ne)
- `settledAmount`  (gt, ge, lt, le, eq, ne)
- `operation`    (in, nin, eq, ne)
- `source`   (in, nin, eq, ne)
- `batchNumber`  (ct, nct, eq, ne)
- `payaccountLastfour`   (nct, ct)
- `payaccountType`   (ne, eq, in, nin)
- `customerFirstname`   (ct, nct, eq, ne)
- `customerLastname`    (ct, nct, eq, ne)
- `customerName`   (ct, nct)
- `customerId`  (eq, ne)
- `customerNumber`  (ct, nct, eq, ne)
- `customerCompanyname`    (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity`    (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity`    (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId`  (eq) *mandatory when entry=org*
- `isHold` (eq, ne)
- `paypointId`  (ne, eq)
- `paypointLegal`  (ne, eq, ct, nct)
- `paypointDba`  (ne, eq, ct, nct)
- `orgName`  (ne, eq, ct, nct)
- `batchId` (ct, nct, eq, neq)
- `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

**List of comparison accepted:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**List of parameters accepted:**

- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `settledAmount(gt)=20` returns all records with a `settledAmount` greater than 20.00.
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListBatches(Entry) -> *payabli.QueryBatchesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of batches for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBatchesRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListBatches(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted:**

- `batchDate` (gt, ge, lt, le, eq, ne)
- `batchNumber` (ne, eq)
- `method` (in, nin, eq, ne)
- `connectorName` (ne, eq, ct, nct)
- `batchAmount` (gt, ge, lt, le, eq, ne)
- `feeBatchAmount` (gt, ge, lt, le, eq, ne)
- `netBatchAmount` (gt, ge, lt, le, eq, ne)
- `releaseAmount` (gt, ge, lt, le, eq, ne)
- `heldAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `paypointId` (ne, eq)
- `externalPaypointID` (ct, nct, eq, ne)
- `expectedDepositDate` (gt, ge, lt, le, eq, ne)
- `depositDate` (gt, ge, lt, le, eq, ne)
- `batchRecords` (gt, ge, lt, le, eq, ne)
- `transferId` (ne, eq)
- `transferDate` (gt, ge, lt, le, eq, ne)
- `grossAmount` (gt, ge, lt, le, eq, ne)
- `chargeBackAmount` (gt, ge, lt, le, eq, ne)
- `returnedAmount` (gt, ge, lt, le, eq, ne)
- `billingFeeAmount` (gt, ge, lt, le, eq, ne)
- `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)
- `netFundedAmount` (gt, ge, lt, le, eq, ne)
- `adjustmentAmount` (gt, ge, lt, le, eq, ne)
- `processor` (ne, eq, ct, nct)
- `transferStatus` (ne, eq, in, nin)

**List of parameters accepted:**
- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `batchAmount(gt)=20` returns all records with a `batchAmount` greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListBatchesOrg(OrgId) -> *payabli.QueryBatchesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of batches for an org. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBatchesOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListBatchesOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted:**

- `batchDate` (gt, ge, lt, le, eq, ne)
- `batchNumber` (ne, eq)
- `method` (in, nin, eq, ne)
- `connectorName` (ne, eq, ct, nct)
- `batchAmount` (gt, ge, lt, le, eq, ne)
- `feeBatchAmount` (gt, ge, lt, le, eq, ne)
- `netBatchAmount` (gt, ge, lt, le, eq, ne)
- `releaseAmount` (gt, ge, lt, le, eq, ne)
- `heldAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `paypointId` (ne, eq)
- `externalPaypointID` (ct, nct, eq, ne)
- `expectedDepositDate` (gt, ge, lt, le, eq, ne)
- `depositDate` (gt, ge, lt, le, eq, ne)
- `batchRecords` (gt, ge, lt, le, eq, ne)
- `transferId` (ne, eq)
- `transferDate` (gt, ge, lt, le, eq, ne)
- `grossAmount` (gt, ge, lt, le, eq, ne)
- `chargeBackAmount` (gt, ge, lt, le, eq, ne)
- `returnedAmount` (gt, ge, lt, le, eq, ne)
- `billingFeeAmount` (gt, ge, lt, le, eq, ne)
- `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)
- `netFundedAmount` (gt, ge, lt, le, eq, ne)
- `adjustmentAmount` (gt, ge, lt, le, eq, ne)
- `processor` (ne, eq, ct, nct)
- `transferStatus` (ne, eq, in, nin)

**List of parameters accepted:**
- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `batchAmount(gt)=20` returns all records with a `batchAmount` greater than 20.00      
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListBatchesOut(Entry) -> *payabli.QueryBatchesOutResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of MoneyOut batches for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBatchesOutRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListBatchesOut(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted**:

- `batchDate` (gt, ge, lt, le, eq, ne)
- `batchNumber` (ne, eq)
- `batchAmount` (gt, ge, lt, le, eq, ne)
- `parentOrgId` (ne, eq, nin, in)
- `status` (in, nin, eq, ne)
- `orgId` (eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `paypointId` (ne, eq)
- `externalPaypointID` (ct, nct, eq, ne)
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListBatchesOutOrg(OrgId) -> *payabli.QueryBatchesOutResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of MoneyOut batches for an org. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListBatchesOutOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListBatchesOutOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted**:

- `batchDate` (gt, ge, lt, le, eq, ne)
- `batchNumber` (ne, eq)
- `batchAmount` (gt, ge, lt, le, eq, ne)
- `parentOrgId` (ne, eq, nin, in)
- `status` (in, nin, eq, ne)
- `orgId` (eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `paypointId` (ne, eq)
- `externalPaypointID` (ct, nct, eq, ne)
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListChargebacks(Entry) -> *payabli.QueryChargebacksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a list of chargebacks and returned transactions for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListChargebacksRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListChargebacks(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

**List of field names accepted:**
- `chargebackDate` (gt, ge, lt, le, eq, ne)
- `transId`  (ne, eq, ct, nct)
- `method`   (in, nin, eq, ne)
- `netAmount`  (gt, ge, lt, le, eq, ne)
- `reasonCode`   (in, nin, eq, ne)
- `reason`  (ct, nct, eq, ne)
- `replyDate` (gt, ge, lt, le, eq, ne)
- `caseNumber`  (ct, nct, eq, ne)
- `status`   (in, nin, eq, ne)
- `accountType`   (in, nin, eq, ne)
- `payaccountLastfour`   (nct, ct)
- `payaccountType`   (ne, eq, in, nin)
- `customerFirstname`   (ct, nct, eq, ne)
- `customerLastname`    (ct, nct, eq, ne)
- `customerName`   (ct, nct)
- `customerId`  (eq, ne)
- `customerNumber`  (ct, nct, eq, ne)
- `customerCompanyname`    (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity`    (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity`    (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId`  (eq) *mandatory when entry=org*
- `paypointId`  (ne, eq)
- `paypointLegal`  (ne, eq, ct, nct)
- `paypointDba`  (ne, eq, ct, nct)
- `orgName`  (ne, eq, ct, nct)
- `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

**List of comparison accepted - enclosed between parentheses:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**List of parameters accepted:**
- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListChargebacksOrg(OrgId) -> *payabli.QueryChargebacksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of chargebacks and returned transactions for an org. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListChargebacksOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListChargebacksOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info> See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

**List of field names accepted:**

- `chargebackDate` (gt, ge, lt, le, eq, ne)
- `transId`  (ne, eq, ct, nct)
- `method`   (in, nin, eq, ne)
- `netAmount`  (gt, ge, lt, le, eq, ne)
- `reasonCode`   (in, nin, eq, ne)
- `reason`  (ct, nct, eq, ne)
- `replyDate` (gt, ge, lt, le, eq, ne)
- `caseNumber`  (ct, nct, eq, ne)
- `status`   (in, nin, eq, ne)
- `accountType`   (in, nin, eq, ne)
- `payaccountLastfour`   (nct, ct)
- `payaccountType`   (ne, eq, in, nin)
- `customerFirstname`   (ct, nct, eq, ne)
- `customerLastname`    (ct, nct, eq, ne)
- `customerName`   (ct, nct)
- `customerId`  (eq, ne)
- `customerNumber`  (ct, nct, eq, ne)
- `customerCompanyname`    (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity`    (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity`    (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId`  (eq) *mandatory when entry=org*
- `paypointId`  (ne, eq)
- `paypointLegal`  (ne, eq, ct, nct)
- `paypointDba`  (ne, eq, ct, nct)
- `orgName`  (ne, eq, ct, nct)
- `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

**List of comparison accepted - enclosed between parentheses:**

- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**List of parameters accepted:**
- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListCustomers(Entry) -> *payabli.QueryCustomerResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a list of customers for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListCustomersRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListCustomers(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more details.

**List of Accepted Field Names:**

- `createdDate` (gt, ge, lt, le, eq, ne)
- `customernumber` (ne, eq, ct, nct)
- `firstname` (ne, eq, ct, nct)
- `lastname` (ne, eq, ct, nct)
- `name` (ct, nct)
- `address` (ne, eq, ct, nct)
- `city` (ne, eq, ct, nct)
- `country` (ne, eq, ct, nct)
- `zip` (ne, eq, ct, nct)
- `state` (ne, eq, ct, nct)
- `shippingaddress` (ne, eq, ct, nct)
- `shippingcity` (ne, eq, ct, nct)
- `shippingcountry` (ne, eq, ct, nct)
- `shippingzip` (ne, eq, ct, nct)
- `shippingstate` (ne, eq, ct, nct)
- `phone` (ne, eq, ct, nct)
- `email` (ne, eq, ct, nct)
- `company` (ne, eq, ct, nct)
- `username` (ne, eq, ct, nct)
- `balance` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name
- `orgId` (eq) *mandatory when entry=org*
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

**List of Accepted Comparisons:**

- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**Accepted Parameters:**
- `limitRecord`: Max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: Initial record in query

**Example Usage:**
`balance(gt)=20` will return all records with a balance greater than 20.00.
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListCustomersOrg(OrgId) -> *payabli.QueryCustomerResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a list of customers for an org. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListCustomersOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListCustomersOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more details.

**List of Accepted Field Names:**

- `createdDate` (gt, ge, lt, le, eq, ne)
- `customernumber` (ne, eq, ct, nct)
- `firstname` (ne, eq, ct, nct)
- `lastname` (ne, eq, ct, nct)
- `name` (ct, nct)
- `address` (ne, eq, ct, nct)
- `city` (ne, eq, ct, nct)
- `country` (ne, eq, ct, nct)
- `zip` (ne, eq, ct, nct)
- `state` (ne, eq, ct, nct)
- `shippingaddress` (ne, eq, ct, nct)
- `shippingcity` (ne, eq, ct, nct)
- `shippingcountry` (ne, eq, ct, nct)
- `shippingzip` (ne, eq, ct, nct)
- `shippingstate` (ne, eq, ct, nct)
- `phone` (ne, eq, ct, nct)
- `email` (ne, eq, ct, nct)
- `company` (ne, eq, ct, nct)
- `username` (ne, eq, ct, nct)
- `balance` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name
- `orgId` (eq) *mandatory when entry=org*
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

**List of Accepted Comparisons:**

- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**Accepted Parameters:**
- `limitRecord`: Max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: Initial record in query

**Example Usage:**
`balance(gt)=20` will return all records with a balance greater than 20.00.
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListNotificationReports(Entry) -> *payabli.QueryResponseNotificationReports</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of all reports generated in the last 60 days for a single entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListNotificationReportsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListNotificationReports(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `reportName` (ct, nct, eq, ne)
- `createdAt` (gt, ge, lt, le, eq, ne)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: reportName(ct)=tr  return all records containing the string "tr"
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListNotificationReportsOrg(OrgId) -> *payabli.QueryResponseNotificationReports</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of all reports generated in the last 60 days for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListNotificationReportsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListNotificationReportsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query <Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `reportName` (ct, nct, eq, ne)
- `createdAt` (gt, ge, lt, le, eq, ne)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: reportName(ct)=tr  return all records containing the string "tr"
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListNotifications(Entry) -> *payabli.QueryResponseNotifications</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of notifications for an entrypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListNotificationsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListNotifications(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `frequency` (in, nin,ne, eq)
- `method` (in, nin, eq, ne)
- `event` (in, nin, eq, ne)
- `target` (ct, nct, eq, ne)
- `status` (eq, ne)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: totalAmount(gt)=20  return all records with totalAmount greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListNotificationsOrg(OrgId) -> *payabli.QueryResponseNotifications</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Return a list of notifications for an organization. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListNotificationsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListNotificationsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `frequency` (in, nin,ne, eq)
- `method` (in, nin, eq, ne)
- `event` (in, nin, eq, ne)
- `target` (ct, nct, eq, ne)
- `status` (eq, ne)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: totalAmount(gt)=20  return all records with totalAmount greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListOrganizations(OrgId) -> *payabli.ListOrganizationsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a list of an organization's suborganizations and their full details such as orgId, users, and settings. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListOrganizationsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListOrganizations(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
**List of field names accepted:**

- `createdAt` (gt, ge, lt, le, eq, ne)
- `startDate` (gt, ge, lt, le, eq, ne)
- `dbaname`  (ct, nct)
- `legalname`  (ct, nct)
- `ein`  (ct, nct)
- `address`  (ct, nct)
- `city`  (ct, nct)
- `state`  (ct, nct)
- `phone`  (ct, nct)
- `mcc`  (ct, nct)
- `owntype`  (ct, nct)
- `ownerName`  (ct, nct)
- `contactName`  (ct, nct)
- `orgParentname`  (ct, nct)
- `boardingId` (eq, ne) 
- `entryName`  (ct, nct)

**List of comparison accepted - enclosed between parentheses:**

- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array
- `nin` => not inside array

**List of parameters accepted:**

- `limitRecord` : max number of records for query (default="20", "0" or negative value for all)
- `fromRecord` : initial record in query

Example: `dbaname(ct)=hoa` returns all records with a `dbaname` containing "hoa"
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListPayout(Entry) -> *payabli.QueryPayoutTransaction</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a list of money out transactions (payouts) for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListPayoutRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListPayout(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

List of field names accepted:

  - `status` (in, nin, eq, ne)
  - `transactionDate` (gt, ge, lt, le, eq, ne)
  - `billNumber` (ct, nct)
  - `vendorNumber` (ct, nct, eq, ne)
  - `vendorName` (ct, nct, eq, ne)
  - `paymentMethod` (ct, nct, eq, ne, in, nin)
  - `paymentId` (ct, nct, eq, ne)
  - `parentOrgId` (ne, eq, nin, in)
  - `batchNumber` (ct, nct, eq, ne)
  - `totalAmount` (gt, ge, lt, le, eq, ne)
  - `paypointLegal` (ne, eq, ct, nct)
  - `paypointDba` (ne, eq, ct, nct)
  - `accountId` (ne, eq, ct, nct)
  - `orgName` (ne, eq, ct, nct)
  - `externalPaypointID` (ct, nct, eq, ne)
  - `paypointId` (eq, ne)
  - `vendorId` (eq, ne)
  - `vendorEIN` (ct, nct, eq, ne)
  - `vendorPhone` (ct, nct, eq, ne)
  - `vendorEmail` (ct, nct, eq, ne)
  - `vendorAddress` (ct, nct, eq, ne)
  - `vendorCity` (ct, nct, eq, ne)
  - `vendorState` (ct, nct, eq, ne)
  - `vendorCountry` (ct, nct, eq, ne)
  - `vendorZip` (ct, nct, eq, ne)
  - `vendorMCC` (ct, nct, eq, ne)
  - `vendorLocationCode` (ct, nct, eq, ne)
  - `vendorCustomField1` (ct, nct, eq, ne)
  - `vendorCustomField2` (ct, nct, eq, ne)
  - `comments` (ct, nct)
  - `payaccountCurrency` (ne, eq, in, nin)
  - `remitAddress` (ct, nct)
  - `source` (ct, nct, eq, ne)
  - `updatedOn` (gt, ge, lt, le, eq, ne)
  - `feeAmount` (gt, ge, lt, le, eq, ne)
  - `lotNumber` (ct, nct)
  - `customerVendorAccount` (ct, nct, eq, ne)
  - `batchId` (eq, ne)
  - `AchTraceNumber` (eq, ne)
  - `payoutProgram`(eq, ne) the options are `managed` or `odp`. For example, `payoutProgram(eq)=managed` returns all records with a `payoutProgram` equal to `managed`. 

  List of comparison accepted - enclosed between parentheses:
  - eq or empty => equal
  - gt => greater than
  - ge => greater or equal
  - lt => less than
  - le => less or equal
  - ne => not equal
  - ct => contains
  - nct => not contains
  - in => inside array separated by \"|\"
  - nin => not inside array separated by \"|\"

  List of parameters accepted:

  - limitRecord : max number of records for query (default=\"20\", \"0\" or negative value for all)
  - fromRecord : initial record in query
  - sortBy : indicate field name and direction to sort the results

  Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00

  Example: `sortBy=desc(netamount)` returns all records sorted by `netAmount` descending
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListPayoutOrg(OrgId) -> *payabli.QueryPayoutTransaction</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a list of money out transactions (payouts) for an organization. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListPayoutOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListPayoutOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
List of field names accepted:
  
  - `status` (in, nin, eq, ne)
  - `transactionDate` (gt, ge, lt, le, eq, ne)
  - `billNumber` (ct, nct)
  - `vendorNumber` (ct, nct, eq, ne)
  - `vendorName` (ct, nct, eq, ne)
  - `parentOrgId` (ne, eq, nin, in)
  - `paymentMethod` (ct, nct, eq, ne, in, nin)
  - `paymentId` (ct, nct, eq, ne)
  - `batchNumber` (ct, nct, eq, ne)
  - `totalAmount` (gt, ge, lt, le, eq, ne)
  - `paypointLegal` (ne, eq, ct, nct)
  - `paypointDba` (ne, eq, ct, nct)
  - `accountId` (ne, eq, ct, nct)
  - `orgName` (ne, eq, ct, nct)
  - `externalPaypointID` (ct, nct, eq, ne)
  - `paypointId` (eq, ne)
  - `vendorId` (eq, ne)
  - `vendorEIN` (ct, nct, eq, ne)
  - `vendorPhone` (ct, nct, eq, ne)
  - `vendorEmail` (ct, nct, eq, ne)
  - `vendorAddress` (ct, nct, eq, ne)
  - `vendorCity` (ct, nct, eq, ne)
  - `vendorState` (ct, nct, eq, ne)
  - `vendorCountry` (ct, nct, eq, ne)
  - `vendorZip` (ct, nct, eq, ne)
  - `vendorMCC` (ct, nct, eq, ne)
  - `vendorLocationCode` (ct, nct, eq, ne)
  - `vendorCustomField1` (ct, nct, eq, ne)
  - `vendorCustomField2` (ct, nct, eq, ne)
  - `comments` (ct, nct)
  - `payaccountCurrency` (ne, eq, in, nin)
  - `remitAddress` (ct, nct)
  - `source` (ct, nct, eq, ne)
  - `updatedOn` (gt, ge, lt, le, eq, ne)
  - `feeAmount` (gt, ge, lt, le, eq, ne)
  - `lotNumber` (ct, nct)
  - `customerVendorAccount` (ct, nct, eq, ne)
  - `batchId` (eq, ne)
  - `AchTraceNumber` (eq, ne)
  - `payoutProgram`(eq, ne) the options are `managed` or `odp`. For example, `payoutProgram(eq)=managed` returns all records with a `payoutProgram` equal to `managed`.

  List of comparison accepted - enclosed between parentheses:
  - eq or empty => equal
  - gt => greater than
  - ge => greater or equal
  - lt => less than
  - le => less or equal
  - ne => not equal
  - ct => contains
  - nct => not contains
  - in => inside array separated by \"|\"
  - nin => not inside array separated by \"|\"

  List of parameters accepted:

  - limitRecord : max number of records for query (default=\"20\", \"0\" or negative value for all)
  - fromRecord : initial record in query
  - sortBy : indicate field name and direction to sort the results

  Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00

  Example: `sortBy=desc(netamount)` returns all records sorted by `netAmount` descending
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListPaypoints(OrgId) -> *payabli.QueryEntrypointResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of paypoints in an organization. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListPaypointsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListPaypoints(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
**List of field names accepted:**

- `createdAt` (gt, ge, lt, le, eq, ne)
- `lastModified` (gt, ge, lt, le, eq, ne)
- `startDate` (gt, ge, lt, le, eq, ne)
- `dbaname`  (ct, nct)
- `status` (eq, ne)
- `legalname`  (ct, nct)
- `externalPaypointID` (ct, nct)
- `ein`  (ct, nct)
- `address`  (ct, nct)
- `city`  (ct, nct)
- `state`  (ct, nct)
- `phone`  (ct, nct)
- `mcc`  (ct, nct)
- `owntype`  (ct, nct)
- `ownerName`  (ct, nct)
- `contactName`  (ct, nct)
- `paypointId` (eq, ne)
- `orgParentname`  (ct, nct, in, nin)
- `boardingId` (eq, ne) 
- `entryName`  (ct, nct)
- `externalOrgID` (ct, nct)

**List of comparison accepted - enclosed between parentheses:**

- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array
- `nin` => not inside array

**List of parameters accepted:**

- `limitRecord` : max number of records for query (default="20", "0" or negative value for all)
- `fromRecord` : initial record in query

Example: `dbaname(ct)=hoa` returns all records with a `dbaname` containing "hoa"
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListSettlements(Entry) -> *payabli.QueryResponseSettlements</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of settled transactions for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListSettlementsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListSettlements(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted:**

- `settlementDate` (gt, ge, lt, le, eq, ne)
- `depositDate` (gt, ge, lt, le, eq, ne)
- `transId`  (ne, eq, ct, nct)
- `gatewayTransId`  (ne, eq, ct, nct)
- `method`   (in, nin, eq, ne)
- `settledAmount`  (gt, ge, lt, le, eq, ne)
- `operation`    (in, nin, eq, ne)
- `source`   (in, nin, eq, ne)
- `batchNumber`  (ct, nct, eq, ne)
- `payaccountLastfour`   (nct, ct)
- `payaccountType`   (ne, eq, in, nin)
- `customerFirstname`   (ct, nct, eq, ne)
- `customerLastname`    (ct, nct, eq, ne)
- `customerName`   (ct, nct)
- `customerId`  (eq, ne)
- `customerNumber`  (ct, nct, eq, ne)
- `customerCompanyname`    (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity`    (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity`    (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId`  (eq) *mandatory when entry=org*
- `isHold` (eq, ne)
- `paypointId`  (ne, eq)
- `paypointLegal`  (ne, eq, ct, nct)
- `paypointDba`  (ne, eq, ct, nct)
- `orgName`  (ne, eq, ct, nct)
- `batchId` (ct, nct, eq, neq)
- `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

**List of comparison accepted:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**List of parameters accepted:**

- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `settledAmount(gt)=20` returns all records with a `settledAmount` greater than 20.00.
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListSettlementsOrg(OrgId) -> *payabli.QueryResponseSettlements</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of settled transactions for an organization. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListSettlementsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListSettlementsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted:**

- `settlementDate` (gt, ge, lt, le, eq, ne)
- `depositDate` (gt, ge, lt, le, eq, ne)
- `transId`  (ne, eq, ct, nct)
- `gatewayTransId`  (ne, eq, ct, nct)
- `method`   (in, nin, eq, ne)
- `settledAmount`  (gt, ge, lt, le, eq, ne)
- `operation`    (in, nin, eq, ne)
- `source`   (in, nin, eq, ne)
- `batchNumber`  (ct, nct, eq, ne)
- `payaccountLastfour`   (nct, ct)
- `payaccountType`   (ne, eq, in, nin)
- `customerFirstname`   (ct, nct, eq, ne)
- `customerLastname`    (ct, nct, eq, ne)
- `customerName`   (ct, nct)
- `customerId`  (eq, ne)
- `customerNumber`  (ct, nct, eq, ne)
- `customerCompanyname`    (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity`    (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity`    (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId`  (eq) *mandatory when entry=org*
- `isHold` (eq, ne)
- `paypointId`  (ne, eq)
- `paypointLegal`  (ne, eq, ct, nct)
- `paypointDba`  (ne, eq, ct, nct)
- `orgName`  (ne, eq, ct, nct)
- `batchId` (ct, nct, eq, neq)
- `additional-xxx`  (ne, eq, ct, nct) where xxx is the additional field name

**List of comparison accepted:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**List of parameters accepted:**

- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `settledAmount(gt)=20` returns all records with a `settledAmount` greater than 20.00.
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListSubscriptions(Entry) -> *payabli.QuerySubscriptionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of subscriptions for a single paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListSubscriptionsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListSubscriptions(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.
      
**List of field names accepted:**

- `startDate` (gt, ge, lt, le, eq, ne)
- `endDate` (gt, ge, lt, le, eq, ne)
- `nextDate` (gt, ge, lt, le, eq, ne)
- `frequency` (in, nin, ne, eq)
- `method` (in, nin, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `feeAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `untilcancelled` (eq, ne)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `payaccountCurrency` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq)
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `externalPaypointId` (ct, nct, ne, eq)
- `subId` (eq, ne)
- `orderDescription` (ct, nct)
- `cycles` (eq, ne, gt, ge, lt, le)
- `leftcycles` (eq, ne, gt, ge, lt, le)
- `createdAt` (eq, ne, gt, ge, lt, le)
- `updatedOn` (eq, ne, gt, ge, lt, le)
- `invoiceNumber` (ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name  

**List of comparison operators accepted:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array
- `nin` => not inside array
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListSubscriptionsOrg(OrgId) -> *payabli.QuerySubscriptionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a list of subscriptions for a single org. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListSubscriptionsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListSubscriptionsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.
      
**List of field names accepted:**

- `startDate` (gt, ge, lt, le, eq, ne)
- `endDate` (gt, ge, lt, le, eq, ne)
- `nextDate` (gt, ge, lt, le, eq, ne)
- `frequency` (in, nin, ne, eq)
- `method` (in, nin, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `feeAmount` (gt, ge, lt, le, eq, ne)
- `status` (in, nin, eq, ne)
- `untilcancelled` (eq, ne)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `payaccountCurrency` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `orgId` (eq)
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `externalPaypointId` (ct, nct, ne, eq)
- `subId` (eq, ne)
- `orderDescription` (ct, nct)
- `cycles` (eq, ne, gt, ge, lt, le)
- `leftcycles` (eq, ne, gt, ge, lt, le)
- `createdAt` (eq, ne, gt, ge, lt, le)
- `updatedOn` (eq, ne, gt, ge, lt, le)
- `invoiceNumber` (ct, nct)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name  

**List of comparison operators accepted:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array
- `nin` => not inside array      
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListTransactions(Entry) -> *payabli.QueryResponseTransactions</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of transactions for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
By default, this endpoint returns only transactions from the last 60 days. To query transactions outside of this period, include `transactionDate` filters.
For example, this request parameters filter for transactions between April 01, 2024 and April 09, 2024. 
``` curl --request GET \
  --url https://sandbox.payabli.com/api/Query/transactions/org/1?limitRecord=20&fromRecord=0&transactionDate(ge)=2024-04-01T00:00:00&transactionDate(le)=2024-04-09T23:59:59\
  --header 'requestToken: <api-key>'

  ```
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListTransactionsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListTransactions(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted:**

- `transactionDate` (gt, ge, lt, le, eq, ne)
- `transId` (ne, eq, ct, nct, in, nin)
- `gatewayTransId` (ne, eq, ct, nct)
- `orderId` (ne, eq)
- `scheduleId` (ne, eq)
- `returnId` (ne, eq)
- `refundId` (ne, eq)
- `idTrans` (ne, eq)
- `orgId` (ne, eq)
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `externalPaypointId` (ct, nct, eq, ne)
- `method` (in, nin, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `feeAmount` (gt, ge, lt, le, eq, ne)
- `operation` (in, nin, eq, ne)
- `source` (in, nin, eq, ne, ct, nct)
- `status` (in, nin, eq, ne)
- `settlementStatus` (in, nin, eq, ne)
- `batchNumber` (nct, ct)
- `invoiceNumber` (ct, nct)
- `ipAddress` (eq, ne)
- `authCode` (ct, nct)
- `orderDescription` (ct, nct)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `payaccountCurrency` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `deviceId` (ct, nct, in, nin, eq, ne)
- `AchSecCode` ( ct, nct, in, nin, eq, ne)
- `AchHolderType` (ct, nct, in, nin, eq, and ne)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name related to customer data
- 'invoiceAdditional-xxx' (ne, eq, ct, nct) where xxx is the additional field name related to invoice data

**List of comparison operators accepted:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array
- `nin` => not inside array      
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListTransactionsOrg(OrgId) -> *payabli.QueryResponseTransactions</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>


Retrieve a list of transactions for an organization. Use filters to
limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.


By default, this endpoint returns only transactions from the last 60 days. To query transactions outside of this period, include `transactionDate` filters.

For example, this request parameters filter for transactions between April 01, 2024 and April 09, 2024. 

```
curl --request GET \
  --url https://sandbox.payabli.com/api/Query/transactions/org/1?limitRecord=20&fromRecord=0&transactionDate(ge)=2024-04-01T00:00:00&transactionDate(le)=2024-04-09T23:59:59\
  --header 'requestToken: <api-key>'

  ```
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListTransactionsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListTransactionsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.

**List of field names accepted:**

- `transactionDate` (gt, ge, lt, le, eq, ne)
- `transId` (ne, eq, ct, nct, in, nin)
- `gatewayTransId` (ne, eq, ct, nct)
- `orderId` (ne, eq)
- `scheduleId` (ne, eq)
- `returnId` (ne, eq)
- `refundId` (ne, eq)
- `idTrans` (ne, eq)
- `orgId` (ne, eq)
- `paypointId` (ne, eq)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)
- `externalPaypointId` (ct, nct, eq, ne)
- `method` (in, nin, eq, ne)
- `totalAmount` (gt, ge, lt, le, eq, ne)
- `netAmount` (gt, ge, lt, le, eq, ne)
- `feeAmount` (gt, ge, lt, le, eq, ne)
- `operation` (in, nin, eq, ne)
- `source` (in, nin, eq, ne, ct, nct)
- `status` (in, nin, eq, ne)
- `settlementStatus` (in, nin, eq, ne)
- `batchNumber` (nct, ct)
- `invoiceNumber` (ct, nct)
- `authCode` (ct, nct)
- `orderDescription` (ct, nct)
- `payaccountLastfour` (nct, ct)
- `payaccountType` (ne, eq, in, nin)
- `payaccountCurrency` (ne, eq, in, nin)
- `customerFirstname` (ct, nct, eq, ne)
- `customerLastname` (ct, nct, eq, ne)
- `customerName` (ct, nct)
- `customerId` (eq, ne)
- `customerNumber` (ct, nct, eq, ne)
- `customerCompanyname` (ct, nct, eq, ne)
- `customerAddress` (ct, nct, eq, ne)
- `customerCity` (ct, nct, eq, ne)
- `customerZip` (ct, nct, eq, ne)
- `customerState` (ct, nct, eq, ne)
- `customerCountry` (ct, nct, eq, ne)
- `customerPhone` (ct, nct, eq, ne)
- `customerEmail` (ct, nct, eq, ne)
- `customerShippingAddress` (ct, nct, eq, ne)
- `customerShippingCity` (ct, nct, eq, ne)
- `customerShippingZip` (ct, nct, eq, ne)
- `customerShippingState` (ct, nct, eq, ne)
- `customerShippingCountry` (ct, nct, eq, ne)
- `deviceId` (ct, nct, in, nin, eq, ne)
- `AchSecCode` ( ct, nct, in, nin, eq, ne)
- `AchHolderType`` (ct, nct, in, nin, eq, and ne)
- `additional-xxx` (ne, eq, ct, nct) where xxx is the additional field name related to customer data
- 'invoiceAdditional-xxx' (ne, eq, ct, nct) where xxx is the additional field name related to invoice data

**List of comparison operators accepted:**
- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array
- `nin` => not inside array
  
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListTransferDetails(Entry, TransferId) -> *payabli.QueryTransferDetailResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of transfer details records for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListTransfersPaypointRequest{}
client.Query.ListTransferDetails(
        context.TODO(),
        "47862acd",
        123456,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**transferId:** `int` — The numeric identifier for the transfer, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*payabli.LimitRecord` 
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter
the query. 

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>

See [Filters and Conditions
Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference)
for more information.


**List of field names accepted:**

  - `grossAmount` (gt, ge, lt, le, eq, ne)
  - `chargeBackAmount` (gt, ge, lt, le, eq, ne)
  - `returnedAmount` (gt, ge, lt, le, eq, ne)
  - `billingFeeAmount` (gt, ge, lt, le, eq, ne)
  - `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)
  - `netFundedAmount` (gt, ge, lt, le, eq, ne)
  - `adjustmentAmount` (gt, ge, lt, le, eq, ne)
  - `splitFundingAmount` (gt, ge, lt, le, eq, ne)
  - `operation` (in, nin, eq, ne)
  - `transactionId` (eq, ne, in, nin)
  - `category` (eq, ne, ct, nct)
  - `type` (eq, ne, in, nin)
  - `method` (eq, ne, in, nin)
  
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListTransfers(Entry) -> *payabli.TransferQueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of transfers for a paypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListTransfersRequest{
        FromRecord: payabli.Int(
            0,
        ),
        LimitRecord: payabli.Int(
            20,
        ),
    }
client.Query.ListTransfers(
        context.TODO(),
        "47862acd",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query. See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
List of field names accepted:

  - `transferDate` (gt, ge, lt, le, eq, ne)
  - `grossAmount` (gt, ge, lt, le, eq, ne)
  - `chargeBackAmount` (gt, ge, lt, le, eq, ne)
  - `returnedAmount` (gt, ge, lt, le, eq, ne)
  - `billingFeeAmount` (gt, ge, lt, le, eq, ne)
  - `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)
  - `netFundedAmount` (gt, ge, lt, le, eq, ne)
  - `adjustmentAmount` (gt, ge, lt, le, eq, ne)
  - `processor` (ne, eq, ct, nct)
  - `transferStatus` (ne, eq, in, nin)
  - `batchNumber` (ne, eq, ct, nct)
  - `batchId` (ne, eq, in, nin)
  - `transferId` (in, nin, eq, ne)
  - `bankAccountNumber` (ct, nct, ne, eq)
  - `bankRoutingNumber` (ct, nct, ne, eq)
  - `batchCurrency` (in, nin, ne, eq)
  - `parentOrgName` (ct, nct, ne, eq)
  - `parentOrgId` (ct, nct, ne, eq)
  - `externalPaypointID` (ct, nct)
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListTransfersOrg(OrgId) -> *payabli.TransferQueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of transfers for an org. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListTransfersRequestOrg{
        OrgId: 123,
        FromRecord: payabli.Int(
            0,
        ),
        LimitRecord: payabli.Int(
            20,
        ),
    }
client.Query.ListTransfersOrg(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `payabli.Orgid` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query. See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for more information.
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
List of field names accepted:

  - `transferDate` (gt, ge, lt, le, eq, ne)
  - `grossAmount` (gt, ge, lt, le, eq, ne)
  - `chargeBackAmount` (gt, ge, lt, le, eq, ne)
  - `returnedAmount` (gt, ge, lt, le, eq, ne)
  - `billingFeeAmount` (gt, ge, lt, le, eq, ne)
  - `thirdPartyPaidAmount` (gt, ge, lt, le, eq, ne)
  - `netFundedAmount` (gt, ge, lt, le, eq, ne)
  - `adjustmentAmount` (gt, ge, lt, le, eq, ne)
  - `processor` (ne, eq, ct, nct)
  - `transferStatus` (ne, eq, in, nin)
  - `batchNumber` (ne, eq, ct, nct)
  - `batchId` (ne, eq, in, nin)
  - `transferId` (in, nin, eq, ne)
  - `bankAccountNumber` (ct, nct, ne, eq)
  - `bankRoutingNumber` (ct, nct, ne, eq)
  - `batchCurrency` (in, nin, ne, eq)
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListUsersOrg(OrgId) -> *payabli.QueryUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get list of users for an org. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListUsersOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListUsersOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

**List of field names accepted:**

- `createdDate` (gt, ge, lt, le, eq, ne)
- `name`  (ne, eq, ct, nct)
- `email`  (ne, eq, ct, nct)
- `status`   (in, nin, eq, ne)
- `role.xxx`  (ne, eq, ct, nct) where xxx is the role field: `roleLabel` or `roleValue`

**List of comparison accepted - enclosed between parentheses:**

- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**List of parameters accepted:**
- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `name(ct)=john`  return all records with name containing 'john'.
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListUsersPaypoint(Entry) -> *payabli.QueryUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get list of users for a paypoint. Use filters to limit results.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListUsersPaypointRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListUsersPaypoint(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query.
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

**List of field names accepted:**

- `createdDate` (gt, ge, lt, le, eq, ne)
- `name`  (ne, eq, ct, nct)
- `email`  (ne, eq, ct, nct)
- `status`   (in, nin, eq, ne)
- `role.xxx`  (ne, eq, ct, nct) where xxx is the role field: `roleLabel` or `roleValue`

**List of comparison accepted - enclosed between parentheses:**

- `eq` or empty => equal
- `gt` => greater than
- `ge` => greater or equal
- `lt` => less than
- `le` => less or equal
- `ne` => not equal
- `ct` => contains
- `nct` => not contains
- `in` => inside array separated by "|"
- `nin` => not inside array separated by "|"

**List of parameters accepted:**
- `limitRecord`: max number of records for query (default="20", "0" or negative value for all)
- `fromRecord`: initial record in query

Example: `name(ct)=john`  return all records with name containing 'john'
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListVendors(Entry) -> *payabli.QueryResponseVendors</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of vendors for an entrypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListVendorsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListVendors(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — The paypoint's entrypoint identifier. [Learn more](/api-reference/api-overview#entrypoint-vs-entry)
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `method` (in, nin, eq, ne)
- `enrollmentStatus` (in,nin, eq, ne)
- `status` (in, nin, eq, ne)
- `vendorNumber` (ct, nct, eq, ne)
- `name` (ct, nct, eq, ne)
- `ein` (ct, nct, eq, ne)
- `phone` (ct, nct, eq, ne)
- `email` (ct, nct, eq, ne)
- `address` (ct, nct, eq, ne)
- `city` (ct, nct, eq, ne)
- `state` (ct, nct, eq, ne)
- `country` (ct, nct, eq, ne)
- `zip` (ct, nct, eq, ne)
- `mcc` (ct, nct, eq, ne)
- `locationCode` (ct, nct, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `parentOrgId` (ne, eq, nin, in)
- `paypointDba` (ne, eq, ct, nct)
- `orgName` (ne, eq, ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListVendorsOrg(OrgId) -> *payabli.QueryResponseVendors</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of vendors for an organization. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListVendorsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListVendorsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `method` (in, nin, eq, ne)
- `enrollmentStatus` (in,nin, eq, ne)
- `status` (in, nin, eq, ne)
- `vendorNumber` (ct, nct, eq, ne)
- `name` (ct, nct, eq, ne)
- `ein` (ct, nct, eq, ne)
- `phone` (ct, nct, eq, ne)
- `email` (ct, nct, eq, ne)
- `address` (ct, nct, eq, ne)
- `city` (ct, nct, eq, ne)
- `state` (ct, nct, eq, ne)
- `country` (ct, nct, eq, ne)
- `zip` (ct, nct, eq, ne)
- `mcc` (ct, nct, eq, ne)
- `locationCode` (ct, nct, eq, ne)
- `paypointLegal` (ne, eq, ct, nct)
- `paypointDba` (ne, eq, ct, nct)
- `parentOrgId` (ne, eq, nin, in)
- `orgName` (ne, eq, ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array separated by "|"
- nin => not inside array separated by "|"

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: `netAmount(gt)=20` returns all records with a `netAmount` greater than 20.00
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListVcards(Entry) -> *payabli.VCardQueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of vcards (virtual credit cards) issued for an entrypoint. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListVcardsRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListVcards(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
List of field names accepted:  

  - `status` (in, nin, eq, ne)  
  - `createdAt` (gt, ge, lt, le, eq, ne)  
  - `cardToken` (ct, nct, eq, ne)  
  - `lastFour` (ct, nct, eq, ne)  
  - `expirationDate` (ct, nct, eq, ne)  
  - `payoutId` (ct, nct, eq, ne, in, nin)  
  - `vendorId` (ct, nct, eq, ne, in, nin)  
  - `miscData1` (ct, nct, eq, ne)  
  - `miscData2` (ct, nct, eq, ne)  
  - `currentUses` (gt, ge, lt, le, eq, ne)  
  - `amount` (gt, ge, lt, le, eq, ne)  
  - `balance` (gt, ge, lt, le, eq, ne)  
  - `paypointLegal` (ne, eq, ct, nct)  
  - `paypointDba` (ne, eq, ct, nct)  
  - `orgName` (ne, eq, ct, nct)  
  - `externalPaypointId` (ct, nct, eq, ne)  
  - `paypointId` (in, nin, eq, ne)  

List of comparison accepted - enclosed between parentheses:  

  - eq or empty => equal  
  - gt => greater than  
  - ge => greater or equal  
  - lt => less than  
  - le => less or equal  
  - ne => not equal  
  - ct => contains  
  - nct => not contains  
  - in => inside array separated by "|"  
  - nin => not inside array separated by "|"
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Query.ListVcardsOrg(OrgId) -> *payabli.VCardQueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a list of vcards (virtual credit cards) issued for an organization. Use filters to limit results. Include the `exportFormat` query parameter to return the results as a file instead of a JSON response.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListVcardsOrgRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Query.ListVcardsOrg(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**exportFormat:** `*payabli.ExportFormat` 
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 

Collection of field names, conditions, and values used to filter the query. 
<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>
List of field names accepted:  

  - `status` (in, nin, eq, ne)  
  - `createdAt` (gt, ge, lt, le, eq, ne)  
  - `cardToken` (ct, nct, eq, ne)  
  - `lastFour` (ct, nct, eq, ne)  
  - `expirationDate` (ct, nct, eq, ne)  
  - `payoutId` (ct, nct, eq, ne, in, nin)  
  - `vendorId` (ct, nct, eq, ne, in, nin)  
  - `miscData1` (ct, nct, eq, ne)  
  - `miscData2` (ct, nct, eq, ne)  
  - `currentUses` (gt, ge, lt, le, eq, ne)  
  - `amount` (gt, ge, lt, le, eq, ne)  
  - `balance` (gt, ge, lt, le, eq, ne)  
  - `paypointLegal` (ne, eq, ct, nct)  
  - `paypointDba` (ne, eq, ct, nct)  
  - `orgName` (ne, eq, ct, nct)  
  - `externalPaypointId` (ct, nct, eq, ne)  
  - `paypointId` (in, nin, eq, ne)  

List of comparison accepted - enclosed between parentheses:  

  - eq or empty => equal  
  - gt => greater than  
  - ge => greater or equal  
  - lt => less than  
  - le => less or equal  
  - ne => not equal  
  - ct => contains  
  - nct => not contains  
  - in => inside array separated by "|"  
  - nin => not inside array separated by "|"
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Statistic
<details><summary><code>client.Statistic.BasicStats(Mode, Freq, Level, EntryId) -> []*payabli.StatBasicExtendedQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves the basic statistics for an organization or a paypoint, for a given time period, grouped by a particular frequency. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.BasicStatsRequest{
        EndDate: payabli.String(
            "2025-11-01",
        ),
        StartDate: payabli.String(
            "2025-11-30",
        ),
    }
client.Statistic.BasicStats(
        context.TODO(),
        1000000,
        "m",
        1,
        "ytd",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**mode:** `string` 

Mode for the request. Allowed values:

- `custom` - Allows you to set a custom date range
- `ytd` - Year To Date
- `mtd` - Month To Date
- `wtd` - Week To Date
- `today` - All current day
- `m12` - Last 12 months
- `d30` - Last 30 days
- `h24` - Last 24 hours
- `lasty` - Last Year
- `lastm` - Last Month
- `lastw` - Last Week
- `yesterday` - Last Day
  
    
</dd>
</dl>

<dl>
<dd>

**freq:** `string` 

Frequency to group series. Allowed values:

- `m` - monthly
- `w` - weekly
- `d` - daily
- `h` - hourly

For example, `w` groups the results by week.
    
</dd>
</dl>

<dl>
<dd>

**level:** `int` 

The entry level for the request: 
  - 0 for Organization
  - 2 for Paypoint
    
</dd>
</dl>

<dl>
<dd>

**entryId:** `int64` — Identifier in Payabli for the entity.
    
</dd>
</dl>

<dl>
<dd>

**endDate:** `*string` 

Used with `custom` mode. The end date for the range. 
Valid formats:
  - YYYY-mm-dd
  - YYYY/mm/dd
  - mm-dd-YYYY
  - mm/dd/YYYY
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` — List of parameters.
    
</dd>
</dl>

<dl>
<dd>

**startDate:** `*string` 

Used with `custom` mode. The start date for the range. 
Valid formats:
   - YYYY-mm-dd
   - YYYY/mm/dd
   -  mm-dd-YYYY
   - mm/dd/YYYY
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Statistic.CustomerBasicStats(Mode, Freq, CustomerId) -> []*payabli.SubscriptionStatsQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves the basic statistics for a customer for a specific time period, grouped by a selected frequency. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.CustomerBasicStatsRequest{}
client.Statistic.CustomerBasicStats(
        context.TODO(),
        998,
        "m",
        "ytd",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**mode:** `string` 

Mode for request. Allowed values:

- `ytd` - Year To Date
- `mtd` - Month To Date
- `wtd` - Week To Date
- `today` - All current day
- `m12` - Last 12 months
- `d30` - Last 30 days
- `h24` - Last 24 hours
- `lasty` - Last Year
- `lastm` - Last Month
- `lastw` - Last Week
- `yesterday` - Last Day
    
</dd>
</dl>

<dl>
<dd>

**freq:** `string` 

Frequency to group series. Allowed values:

- `m` - monthly
- `w` - weekly
- `d` - daily
- `h` - hourly

For example, `w` groups the results by week.
    
</dd>
</dl>

<dl>
<dd>

**customerId:** `int` — Payabli-generated customer ID. Maps to "Customer ID" column in PartnerHub. 
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` — List of parameters.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Statistic.SubStats(Interval, Level, EntryId) -> []*payabli.StatBasicQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves the subscription statistics for a given interval for a paypoint or organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.SubStatsRequest{}
client.Statistic.SubStats(
        context.TODO(),
        1000000,
        "30",
        1,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**interval:** `string` 

Interval to get the data. Allowed values:

- `all` - all intervals
- `30` - 1-30 days
- `60` - 31-60 days
- `90` - 61-90 days
- `plus` - +90 days
    
</dd>
</dl>

<dl>
<dd>

**level:** `int` 

The entry level for the request: 
  - 0 for Organization
  - 2 for Paypoint
    
</dd>
</dl>

<dl>
<dd>

**entryId:** `int64` — Identifier in Payabli for the entity.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` — List of parameters
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Statistic.VendorBasicStats(Mode, Freq, IdVendor) -> []*payabli.StatisticsVendorQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve the basic statistics about a vendor for a given time period, grouped by frequency. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.VendorBasicStatsRequest{}
client.Statistic.VendorBasicStats(
        context.TODO(),
        "m",
        1,
        "ytd",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**mode:** `string` 

Mode for request. Allowed values:

- `ytd` - Year To Date
- `mtd` - Month To Date
- `wtd` - Week To Date
- `today` - All current day
- `m12` - Last 12 months
- `d30` - Last 30 days
- `h24` - Last 24 hours
- `lasty` - Last Year
- `lastm` - Last Month
- `lastw` - Last Week
- `yesterday` - Last Day
    
</dd>
</dl>

<dl>
<dd>

**freq:** `string` 

Frequency to group series. Allowed values:

- `m` - monthly
- `w` - weekly
- `d` - daily
- `h` - hourly

For example, `w` groups the results by week.
    
</dd>
</dl>

<dl>
<dd>

**idVendor:** `int` — Vendor ID.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` — List of parameters
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Subscription
<details><summary><code>client.Subscription.GetSubscription(SubId) -> *payabli.SubscriptionQueryRecords</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a single subscription's details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Subscription.GetSubscription(
        context.TODO(),
        263,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**subId:** `int` — The subscription ID. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Subscription.NewSubscription(request) -> *payabli.AddSubscriptionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a subscription or scheduled payment to run at a specified time and frequency. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RequestSchedule{
        Body: &payabli.SubscriptionRequestBody{
            CustomerData: &payabli.PayorDataRequest{
                CustomerId: payabli.Int64(
                    4440,
                ),
            },
            EntryPoint: payabli.String(
                "f743aed24a",
            ),
            PaymentDetails: &payabli.PaymentDetail{
                ServiceFee: payabli.Float64(
                    0,
                ),
                TotalAmount: 100,
            },
            PaymentMethod: &payabli.RequestSchedulePaymentMethod{
                PayMethodCredit: &payabli.PayMethodCredit{
                    Cardcvv: payabli.String(
                        "123",
                    ),
                    Cardexp: "02/25",
                    CardHolder: payabli.String(
                        "John Cassian",
                    ),
                    Cardnumber: "4111111111111111",
                    Cardzip: payabli.String(
                        "37615",
                    ),
                    Initiator: payabli.String(
                        "payor",
                    ),
                },
            },
            ScheduleDetails: &payabli.ScheduleDetail{
                EndDate: payabli.String(
                    "03-20-2025",
                ),
                Frequency: payabli.FrequencyWeekly.Ptr(),
                PlanId: payabli.Int(
                    1,
                ),
                StartDate: payabli.String(
                    "09-20-2024",
                ),
            },
        },
    }
client.Subscription.NewSubscription(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**forceCustomerCreation:** `*payabli.ForceCustomerCreation` 
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.SubscriptionRequestBody` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Subscription.RemoveSubscription(SubId) -> *payabli.RemoveSubscriptionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a subscription, autopay, or recurring payment and prevents future charges.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Subscription.RemoveSubscription(
        context.TODO(),
        396,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**subId:** `int` — The subscription ID. 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Subscription.UpdateSubscription(SubId, request) -> *payabli.UpdateSubscriptionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates a subscription's details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.RequestUpdateSchedule{
        SetPause: payabli.Bool(
            true,
        ),
    }
client.Subscription.UpdateSubscription(
        context.TODO(),
        231,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**subId:** `int` — The subscription ID. 
    
</dd>
</dl>

<dl>
<dd>

**paymentDetails:** `*payabli.PaymentDetail` — Object describing details of the payment. To skip the payment, set the `totalAmount` to 0. Payments will be paused until the amount is updated to a non-zero value. When `totalAmount` is set to 0, the `serviceFee` must also be set to 0.
    
</dd>
</dl>

<dl>
<dd>

**scheduleDetails:** `*payabli.ScheduleDetail` — Object describing the schedule for subscription
    
</dd>
</dl>

<dl>
<dd>

**setPause:** `*payabli.SetPause` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Templates
<details><summary><code>client.Templates.DeleteTemplate(TemplateId) -> *payabli.PayabliApiResponseTemplateId</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a template by ID. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Templates.DeleteTemplate(
        context.TODO(),
        80,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**templateId:** `float64` — The boarding template ID. Can be found at the end of the boarding template URL in PartnerHub. Example: `https://partner-sandbox.payabli.com/myorganization/boarding/edittemplate/80`. Here, the template ID is `80`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Templates.GetlinkTemplate(TemplateId, IgnoreEmpty) -> *payabli.BoardingLinkApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Generates a boarding link from a boarding template.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Templates.GetlinkTemplate(
        context.TODO(),
        true,
        80,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**templateId:** `float64` — The boarding template ID. Can be found at the end of the boarding template URL in PartnerHub. Example: `https://partner-sandbox.payabli.com/myorganization/boarding/edittemplate/80`. Here, the template ID is `80`.
    
</dd>
</dl>

<dl>
<dd>

**ignoreEmpty:** `bool` — Ignore read-only and empty fields Default is `false`. If `ignoreEmpty` = `false` and any field is empty, then the request returns a failure response. If `ignoreEmpty` = `true`, the request returns the boarding link name regardless of whether fields are empty.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Templates.GetTemplate(TemplateId) -> *payabli.TemplateQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a boarding template's details by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Templates.GetTemplate(
        context.TODO(),
        80,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**templateId:** `float64` — The boarding template ID. Can be found at the end of the boarding template URL in PartnerHub. Example: `https://partner-sandbox.payabli.com/myorganization/boarding/edittemplate/80`. Here, the template ID is `80`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Templates.ListTemplates(OrgId) -> *payabli.TemplateQueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a list of boarding templates for an organization. Use filters to limit results. You can't make a request that includes filters from the API console in the documentation. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ListTemplatesRequest{
        FromRecord: payabli.Int(
            251,
        ),
        LimitRecord: payabli.Int(
            0,
        ),
        SortBy: payabli.String(
            "desc(field_name)",
        ),
    }
client.Templates.ListTemplates(
        context.TODO(),
        123,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**orgId:** `int` — The numeric identifier for organization, assigned by Payabli.
    
</dd>
</dl>

<dl>
<dd>

**fromRecord:** `*int` — The number of records to skip before starting to collect the result set.
    
</dd>
</dl>

<dl>
<dd>

**limitRecord:** `*int` — Max number of records to return for the query. Use `0` or negative value to return all records.
    
</dd>
</dl>

<dl>
<dd>

**parameters:** `map[string]*string` 


Collection of field names, conditions, and values used to filter the query.

<Info>
  **You must remove `parameters=` from the request before you send it, otherwise Payabli will ignore the filters.**

  Because of a technical limitation, you can't make a request that includes filters from the API console on this page. The response won't be filtered. Instead, copy the request, remove `parameters=` and run the request in a different client.

  For example:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?parameters=totalAmount(gt)=1000&limitRecord=20

  should become:

  --url https://api-sandbox.payabli.com/api/Query/transactions/org/236?totalAmount(gt)=1000&limitRecord=20
</Info>


See [Filters and Conditions Reference](/developers/developer-guides/pay-ops-reporting-engine-overview#filters-and-conditions-reference) for help.

List of field names accepted:
- `createdAt` (gt, ge, lt, le, eq, ne)
- `title` (ct, nct)
- `description` (ct, nct)
- `code` (ct, nct)
- `orgParentname` (ct, nct)

List of comparison accepted - enclosed between parentheses:
- eq or empty => equal
- gt => greater than
- ge => greater or equal
- lt => less than
- le => less or equal
- ne => not equal
- ct => contains
- nct => not contains
- in => inside array
- nin => not inside array

List of parameters accepted:
- limitRecord : max number of records for query (default="20", "0" or negative value for all)
- fromRecord : initial record in query

Example: title(ct)=hoa return all records with title containing "hoa"
    
</dd>
</dl>

<dl>
<dd>

**sortBy:** `*string` — The field name to use for sorting results. Use `desc(field_name)` to sort descending by `field_name`, and use `asc(field_name)` to sort ascending by `field_name`.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## TokenStorage
<details><summary><code>client.TokenStorage.AddMethod(request) -> *payabli.AddMethodResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Saves a payment method for reuse. This call exchanges sensitive payment information for a token that can be used to process future transactions. The `ReferenceId` value in the response is the `storedMethodId` to use with transactions.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.AddMethodRequest{
        Body: &payabli.RequestTokenStorage{
            CustomerData: &payabli.PayorDataRequest{
                CustomerId: payabli.Int64(
                    4440,
                ),
            },
            EntryPoint: payabli.String(
                "f743aed24a",
            ),
            FallbackAuth: payabli.Bool(
                true,
            ),
            PaymentMethod: &payabli.RequestTokenStoragePaymentMethod{
                TokenizeCard: &payabli.TokenizeCard{
                    Cardcvv: payabli.String(
                        "123",
                    ),
                    Cardexp: "02/25",
                    CardHolder: "John Doe",
                    Cardnumber: "4111111111111111",
                    Cardzip: payabli.String(
                        "12345",
                    ),
                    Method: "card",
                },
            },
        },
    }
client.TokenStorage.AddMethod(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**achValidation:** `*payabli.AchValidation` 
    
</dd>
</dl>

<dl>
<dd>

**createAnonymous:** `payabli.CreateAnonymous` 
    
</dd>
</dl>

<dl>
<dd>

**forceCustomerCreation:** `*payabli.ForceCustomerCreation` 
    
</dd>
</dl>

<dl>
<dd>

**temporary:** `payabli.Temporary` 
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `*payabli.IdempotencyKey` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.RequestTokenStorage` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.TokenStorage.GetMethod(MethodId) -> *payabli.GetMethodResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves details for a saved payment method.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.GetMethodRequest{
        CardExpirationFormat: payabli.Int(
            1,
        ),
        IncludeTemporary: payabli.Bool(
            false,
        ),
    }
client.TokenStorage.GetMethod(
        context.TODO(),
        "32-8877drt00045632-678",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**methodId:** `string` — The saved payment method ID.
    
</dd>
</dl>

<dl>
<dd>

**cardExpirationFormat:** `*int` 

Format for card expiration dates in the response. 

Accepted values:
  
- 0: default, no formatting. Expiration dates are returned in the format they're saved in.

- 1: MMYY
 
- 2: MM/YY
    
</dd>
</dl>

<dl>
<dd>

**includeTemporary:** `*bool` — When `true`, the request will include temporary tokens in the search and return details for a matching temporary token. The default behavior searches only for permanent tokens.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.TokenStorage.RemoveMethod(MethodId) -> *payabli.PayabliApiResponsePaymethodDelete</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a saved payment method.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.TokenStorage.RemoveMethod(
        context.TODO(),
        "32-8877drt00045632-678",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**methodId:** `string` — The saved payment method ID.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.TokenStorage.UpdateMethod(MethodId, request) -> *payabli.PayabliApiResponsePaymethodDelete</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates a saved payment method.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.UpdateMethodRequest{
        Body: &payabli.RequestTokenStorage{
            CustomerData: &payabli.PayorDataRequest{
                CustomerId: payabli.Int64(
                    4440,
                ),
            },
            EntryPoint: payabli.String(
                "f743aed24a",
            ),
            FallbackAuth: payabli.Bool(
                true,
            ),
            PaymentMethod: &payabli.RequestTokenStoragePaymentMethod{
                TokenizeCard: &payabli.TokenizeCard{
                    Cardcvv: payabli.String(
                        "123",
                    ),
                    Cardexp: "02/25",
                    CardHolder: "John Doe",
                    Cardnumber: "4111111111111111",
                    Cardzip: payabli.String(
                        "12345",
                    ),
                    Method: "card",
                },
            },
        },
    }
client.TokenStorage.UpdateMethod(
        context.TODO(),
        "32-8877drt00045632-678",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**methodId:** `string` — The saved payment method ID.
    
</dd>
</dl>

<dl>
<dd>

**achValidation:** `*payabli.AchValidation` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.RequestTokenStorage` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## User
<details><summary><code>client.User.AddUser(request) -> *payabli.AddUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to add a new user to an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.UserData{}
client.User.AddUser(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*payabli.UserData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.AuthRefreshUser() -> *payabli.PayabliApiResponseUserMfa</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to refresh the authentication token for a user within an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.User.AuthRefreshUser(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.AuthResetUser(request) -> *payabli.AuthResetUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to initiate a password reset for a user within an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.UserAuthResetRequest{}
client.User.AuthResetUser(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**email:** `*payabli.Email` — The user's email address.
    
</dd>
</dl>

<dl>
<dd>

**entry:** `*string` — Identifier for entrypoint originating the request (used by front-end apps)
    
</dd>
</dl>

<dl>
<dd>

**entryType:** `*int` — Type of entry identifier: 0 - partner, 2 - paypoint. This is used by front-end apps, required if an Entry is indicated.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.AuthUser(Provider, request) -> *payabli.PayabliApiResponseMfaBasic</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

This endpoint requires an application API token.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.UserAuthRequest{}
client.User.AuthUser(
        context.TODO(),
        "provider",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**provider:** `string` — Auth provider. This fields is optional and defaults to null for the built-in provider.
    
</dd>
</dl>

<dl>
<dd>

**email:** `*payabli.Email` 
    
</dd>
</dl>

<dl>
<dd>

**entry:** `*string` — Identifier for entry point originating the request (used by front-end apps)
    
</dd>
</dl>

<dl>
<dd>

**entryType:** `*int` — Type of entry identifier: 0 - partner, 2 - paypoint. This is used by front-end apps, required if an Entry is indicated.
    
</dd>
</dl>

<dl>
<dd>

**psw:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**userId:** `*int64` 
    
</dd>
</dl>

<dl>
<dd>

**userTokenId:** `*string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.ChangePswUser(request) -> *payabli.ChangePswUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to change the password for a user within an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.UserAuthPswResetRequest{}
client.User.ChangePswUser(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**psw:** `*string` — New User password
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.DeleteUser(UserId) -> *payabli.DeleteUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to delete a specific user within an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.User.DeleteUser(
        context.TODO(),
        1000000,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**userId:** `int64` — The Payabli-generated `userId` value.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.EditMfaUser(UserId, request) -> *payabli.EditMfaUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to enable or disable multi-factor authentication (MFA) for a user within an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.MfaData{}
client.User.EditMfaUser(
        context.TODO(),
        1000000,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**userId:** `int64` — User Identifier
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.MfaData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.EditUser(UserId, request) -> *payabli.PayabliApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to modify the details of a specific user within an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.UserData{}
client.User.EditUser(
        context.TODO(),
        1000000,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**userId:** `int64` — User Identifier
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.UserData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.GetUser(UserId) -> *payabli.UserQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to retrieve information about a specific user within an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.GetUserRequest{
        Entry: payabli.String(
            "478ae1234",
        ),
    }
client.User.GetUser(
        context.TODO(),
        1000000,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**userId:** `int64` — The Payabli-generated `userId` value.
    
</dd>
</dl>

<dl>
<dd>

**entry:** `*string` — The entrypoint identifier.
    
</dd>
</dl>

<dl>
<dd>

**level:** `*int` — Entry level: 0 - partner, 2 - paypoint
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.LogoutUser() -> *payabli.LogoutUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to log a user out from the system.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.User.LogoutUser(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.ResendMfaCode(Usrname, Entry, EntryType) -> *payabli.PayabliApiResponseMfaBasic</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Resends the MFA code to the user via the selected MFA mode (email or SMS).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.User.ResendMfaCode(
        context.TODO(),
        "Entry",
        1,
        "usrname",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**usrname:** `string` —  
    
</dd>
</dl>

<dl>
<dd>

**entry:** `string` —  
    
</dd>
</dl>

<dl>
<dd>

**entryType:** `int` —  
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.User.ValidateMfaUser(request) -> *payabli.PayabliApiResponseUserMfa</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Use this endpoint to validate the multi-factor authentication (MFA) code for a user within an organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.MfaValidationData{}
client.User.ValidateMfaUser(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**mfaCode:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**mfaValidationCode:** `*payabli.MfaValidationCode` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Vendor
<details><summary><code>client.Vendor.AddVendor(Entry, request) -> *payabli.PayabliApiResponseVendors</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a vendor in an entrypoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.VendorData{
        VendorNumber: payabli.String(
            "1234",
        ),
        Name1: payabli.String(
            "Herman's Coatings and Masonry",
        ),
        Name2: payabli.String(
            "<string>",
        ),
        Ein: payabli.String(
            "12-3456789",
        ),
        Phone: payabli.String(
            "5555555555",
        ),
        Email: payabli.String(
            "example@email.com",
        ),
        Address1: payabli.String(
            "123 Ocean Drive",
        ),
        Address2: payabli.String(
            "Suite 400",
        ),
        City: payabli.String(
            "Miami",
        ),
        State: payabli.String(
            "FL",
        ),
        Zip: payabli.String(
            "33139",
        ),
        Country: payabli.String(
            "US",
        ),
        Mcc: payabli.String(
            "7777",
        ),
        LocationCode: payabli.String(
            "MIA123",
        ),
        Contacts: []*payabli.Contacts{
            &payabli.Contacts{
                ContactName: payabli.String(
                    "Herman Martinez",
                ),
                ContactEmail: payabli.String(
                    "example@email.com",
                ),
                ContactTitle: payabli.String(
                    "Owner",
                ),
                ContactPhone: payabli.String(
                    "3055550000",
                ),
            },
        },
        BillingData: &payabli.BillingData{
            Id: payabli.Int(
                123,
            ),
            BankName: payabli.String(
                "Country Bank",
            ),
            RoutingAccount: payabli.String(
                "123123123",
            ),
            AccountNumber: payabli.String(
                "123123123",
            ),
            TypeAccount: payabli.TypeAccountChecking.Ptr(),
            BankAccountHolderName: payabli.String(
                "Gruzya Adventure Outfitters LLC",
            ),
            BankAccountHolderType: payabli.BankAccountHolderTypeBusiness.Ptr(),
            BankAccountFunction: payabli.Int(
                0,
            ),
        },
        PaymentMethod: payabli.String(
            "managed",
        ),
        VendorStatus: payabli.Int(
            1,
        ),
        RemitAddress1: payabli.String(
            "123 Walnut Street",
        ),
        RemitAddress2: payabli.String(
            "Suite 900",
        ),
        RemitCity: payabli.String(
            "Miami",
        ),
        RemitState: payabli.String(
            "FL",
        ),
        RemitZip: payabli.String(
            "31113",
        ),
        RemitCountry: payabli.String(
            "US",
        ),
        PayeeName1: payabli.String(
            "<string>",
        ),
        PayeeName2: payabli.String(
            "<string>",
        ),
        CustomerVendorAccount: payabli.String(
            "A-37622",
        ),
        InternalReferenceId: payabli.Int64(
            123,
        ),
    }
client.Vendor.AddVendor(
        context.TODO(),
        "8cfec329267",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `string` — Entrypoint identifier.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.VendorData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Vendor.DeleteVendor(IdVendor) -> *payabli.PayabliApiResponseVendors</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a vendor. 
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Vendor.DeleteVendor(
        context.TODO(),
        1,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idVendor:** `int` — Vendor ID.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Vendor.EditVendor(IdVendor, request) -> *payabli.PayabliApiResponseVendors</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates a vendor's information. Send only the fields you need to update.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.VendorData{
        Name1: payabli.String(
            "Theodore's Janitorial",
        ),
    }
client.Vendor.EditVendor(
        context.TODO(),
        1,
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idVendor:** `int` — Vendor ID.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*payabli.VendorData` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Vendor.GetVendor(IdVendor) -> *payabli.VendorQueryRecord</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves a vendor's details.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Vendor.GetVendor(
        context.TODO(),
        1,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idVendor:** `int` — Vendor ID.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Wallet
<details><summary><code>client.Wallet.ConfigureApplePayOrganization(request) -> *payabli.ConfigureApplePayOrganizationApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Configure and activate Apple Pay for a Payabli organization
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ConfigureOrganizationRequestApplePay{
        Cascade: payabli.Bool(
            true,
        ),
        IsEnabled: payabli.Bool(
            true,
        ),
        OrgId: payabli.Int64(
            901,
        ),
    }
client.Wallet.ConfigureApplePayOrganization(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**cascade:** `*payabli.Cascade` 
    
</dd>
</dl>

<dl>
<dd>

**isEnabled:** `*payabli.IsEnabled` 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `*payabli.OrganizationId` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Wallet.ConfigureApplePayPaypoint(request) -> *payabli.ConfigureApplePaypointApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Configure and activate Apple Pay for a Payabli paypoint
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ConfigurePaypointRequestApplePay{
        Entry: payabli.String(
            "8cfec329267",
        ),
        IsEnabled: payabli.Bool(
            true,
        ),
    }
client.Wallet.ConfigureApplePayPaypoint(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `*payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**isEnabled:** `*payabli.IsEnabled` — When `true`, Apple Pay is enabled.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Wallet.ConfigureGooglePayOrganization(request) -> *payabli.ConfigureApplePayOrganizationApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Configure and activate Google Pay for a Payabli organization
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ConfigureOrganizationRequestGooglePay{
        Cascade: payabli.Bool(
            true,
        ),
        IsEnabled: payabli.Bool(
            true,
        ),
        OrgId: payabli.Int64(
            901,
        ),
    }
client.Wallet.ConfigureGooglePayOrganization(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**cascade:** `*payabli.Cascade` 
    
</dd>
</dl>

<dl>
<dd>

**isEnabled:** `*payabli.IsEnabled` 
    
</dd>
</dl>

<dl>
<dd>

**orgId:** `*payabli.OrganizationId` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Wallet.ConfigureGooglePayPaypoint(request) -> *payabli.ConfigureGooglePaypointApiResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Configure and activate Google Pay for a Payabli paypoint
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &payabli.ConfigurePaypointRequestGooglePay{
        Entry: payabli.String(
            "8cfec329267",
        ),
        IsEnabled: payabli.Bool(
            true,
        ),
    }
client.Wallet.ConfigureGooglePayPaypoint(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entry:** `*payabli.Entry` 
    
</dd>
</dl>

<dl>
<dd>

**isEnabled:** `*payabli.IsEnabled` — When `true`, Google Pay is enabled.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>
