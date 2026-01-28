# 📘 Ultimate Guide for SAP OData API_BUSINESS_PARTNER

<div align="center">

![SAP](https://img.shields.io/badge/SAP-0FAAFF?style=for-the-badge&logo=sap&logoColor=white)
![OData](https://img.shields.io/badge/OData-8B4513?style=for-the-badge)
![Business Partner](https://img.shields.io/badge/Business_Partner-4CAF50?style=for-the-badge)

**The Complete Reference for SAP Business Partner API**

*A comprehensive guide for SAP End Users, Functional Consultants, and Technical Developers*

[Overview](#-overview) • [Quick Start](#-quick-start) • [For End Users](#-for-sap-end-users) • [For Functional](#-for-sap-functional-consultants) • [For Technical](#-for-sap-technical-developers) • [FAQ](#-frequently-asked-questions)

</div>

---

## 📋 Table of Contents

1. [What Is This Repository?](#-what-is-this-repository)
2. [Who Should Use This?](#-who-should-use-this)
3. [Repository Files](#-repository-files)
4. [Overview](#-overview)
5. [For SAP End Users](#-for-sap-end-users)
6. [For SAP Functional Consultants](#-for-sap-functional-consultants)
7. [For SAP Technical Developers](#-for-sap-technical-developers)
8. [Understanding the Data Structure](#-understanding-the-data-structure)
9. [Complete Entity Type Reference](#-complete-entity-type-reference)
10. [Business Processes Covered](#-business-processes-covered)
11. [Integration Scenarios](#-integration-scenarios)
12. [Use Cases & Examples](#-use-cases--examples)
13. [Best Practices](#-best-practices)
14. [Troubleshooting](#-troubleshooting)
15. [Frequently Asked Questions](#-frequently-asked-questions)
16. [Glossary](#-glossary)
17. [Additional Resources](#-additional-resources)

---

## 🎯 What Is This Repository?

This repository contains the **complete data structure definition** for SAP's Business Partner API. Think of it as a **detailed blueprint** that shows:

- 📊 **What information** can be stored about business partners (customers, suppliers, contacts)
- 🔗 **How different pieces of information** connect to each other
- ✅ **What rules** must be followed when entering data
- 🔍 **What fields are available** for searching, filtering, and reporting

### In Simple Terms

Imagine you're building a house. Before you start, you need:
- A blueprint showing all rooms (entities)
- Details about each room - size, purpose, connections (properties)
- Rules about construction (constraints and validations)

This repository is that **blueprint for SAP Business Partner data** - it tells you exactly what you can build and how to build it.

---

## 👥 Who Should Use This?

### 🎓 **SAP End Users**
Learn what information is available about customers, suppliers, and contacts. Understand what data you can request in reports and what fields mean.

### 💼 **SAP Functional Consultants**
Use this as a reference for business requirements, data migration, interface design, and training. Map business processes to technical fields.

### 💻 **SAP Technical Developers**
Build integrations, develop custom apps, create APIs, generate database schemas, and validate data structures using this definitive reference.

---

## 📁 Repository Files

| File | Purpose | Audience |
|------|---------|----------|
| **API_BUSINESS_PARTNER_SCHEMA.json** | Complete technical schema with all entity types, properties, and relationships | Technical, Functional |
| **Summary.md** | Detailed xml to json conversion report and technical specifications | Technical |
| **entity_type_index.json** | Quick reference index of all entity types | All |
| **README.md** (this file) | Comprehensive guide for all audiences | All |
| **LICENSE** | Usage terms and conditions | All |

---

## 🌟 Overview

### What is API_BUSINESS_PARTNER?

**API_BUSINESS_PARTNER** is SAP's standardized web service (OData API) for managing business partner master data. It provides a unified way to:

- ✅ Create, read, update, and delete business partner records
- ✅ Manage customer and supplier information
- ✅ Handle contact person details
- ✅ Maintain addresses, phone numbers, emails, and URLs
- ✅ Store bank details and tax information
- ✅ Link business relationships and hierarchies

### What is OData?

**OData (Open Data Protocol)** is like a universal language that different computer systems use to share data. Think of it as:

- 🌐 A **website for data** instead of web pages
- 📖 A **standardized way** to ask for and receive information
- 🔄 Works over the internet using familiar web technology (HTTP)

### What is a Schema?

A **schema** is like a **detailed catalog** that describes:

- 📚 What types of information exist (Entity Types)
- 📝 What details each type contains (Properties)
- 🔗 How different types relate to each other (Associations)
- ✅ What rules govern the data (Constraints)

---

## 👤 For SAP End Users

### What Can You Do With This Information?

As an SAP end user, this schema helps you understand:

#### 1. **Available Data Fields**

Every piece of information you see in SAP has a technical name and specific rules. For example:

| What You See in SAP | Technical Name | What It Means |
|---------------------|----------------|---------------|
| Customer Number | `Customer` | Unique 10-character code for each customer |
| Email Address | `EmailAddress` | Can be up to 241 characters long |
| Phone Number | `PhoneNumber` | Mobile or landline number with country code |
| Business Partner | `BusinessPartner` | Universal ID for any business entity |

#### 2. **Understanding Reports & T-Codes**

When you use standard SAP transactions (T-Codes), you are interacting with the same data this API manages.

| SAP Transaction | Description | API Mapping |
|-----------------|-------------|-------------|
| **BP** | Business Partner Maintenance | `A_BusinessPartner` |
| **FPP1 / FPP2** | Create/Change Contract Partner | `A_BusinessPartner` |
| **FLBPC1 / FLBPC2** | Customer/Supplier Linkage | `A_Customer` / `A_Supplier` |

#### 3. **Data Entry Requirements**

Before entering data, you can check:

- ✅ **Required fields** - marked as `Nullable: false`
- ✅ **Maximum length** - e.g., "Business Partner Name must be max 35 characters"
- ✅ **Format requirements** - e.g., "Country code must be 3 characters"

#### 4. **Common Business Entities You Work With**

| Entity | What It Is | Example |
|--------|-----------|---------|
| **Business Partner** | Any person or company you do business with | Customer, Supplier, Employee |
| **Customer** | Someone who buys from you | ABC Corp (buying goods) |
| **Supplier** | Someone you buy from | XYZ Ltd (selling raw materials) |
| **Contact Person** | Individual representing a company | John Smith at ABC Corp |
| **Address** | Location information | Shipping address, billing address |

### Real-World Example

**Scenario**: You need to add a new customer contact person.

Looking at the schema, you'll know:
- ✅ You need: First Name, Last Name, Business Partner Number
- ✅ Optional: Email (max 241 chars), Phone number (max 30 chars)
- ✅ You can add multiple email addresses and phone numbers
- ✅ One can be marked as "default" or "standard"

### More Real-World Scenarios for End Users

#### Scenario 1: Creating a New Customer

When you use transaction **BP** to create a customer, you're filling in data that corresponds to:

| Screen Field | Technical Entity | Why It Matters |
|--------------|------------------|----------------|
| Name 1 / Name 2 | `OrganizationBPName1` | Company legal name |
| Search Term | `SearchTerm1` | How you'll find them later |
| Street Address | `StreetName`, `HouseNumber` | Delivery and billing |
| City / Postal Code | `CityName`, `PostalCode` | Required for all addresses |
| Country | `Country` | Must be valid 2-letter code (DE, US, GB) |
| Customer Account Group | `CustomerAccountGroup` | Determines number range and field visibility |

#### Scenario 2: Updating Contact Information

Your manager asks: "Update the phone number for customer 1000001."

What happens technically:
1. The system finds BP `1000001`
2. Locates their address (`A_BusinessPartnerAddress`)
3. Finds phone records under that address (`A_AddressPhoneNumber`)
4. Updates the `PhoneNumber` field

**Tip**: Each customer can have multiple addresses, and each address can have multiple phone numbers!

#### Scenario 3: Understanding Customer Flags

Sometimes customers appear "blocked" in the system. Here's what those fields mean:

| Field | What It Means | Impact |
|-------|---------------|--------|
| `DeletionIndicator` = true | Marked for archiving | Can't create new orders |
| `IsMarkedForDeletion` = true | Will be deleted soon | Appears in cleanup reports |
| `OrderIsBlockedForCustomer` = true | Sales orders blocked | No orders allowed |
| `DeliveryIsBlocked` = true | Deliveries blocked | Orders exist but can't ship |
| `BillingIsBlockedForCustomer` = true | Billing blocked | Can ship but can't invoice |

#### Scenario 4: Why Your Report Shows "No Data"

Common reasons and fixes:

| Problem | Likely Cause | How to Check |
|---------|--------------|--------------|
| Customer not found | Wrong account group filter | Check `CustomerAccountGroup` |
| Missing address | Address not yet created | Check `A_BusinessPartnerAddress` exists |
| No sales data | Customer not extended to sales org | Check `A_CustomerSalesArea` |
| No company code data | Customer not extended to company code | Check `A_CustomerCompany` |

### Quick Reference Card for End Users

```
📋 CUSTOMER DATA STRUCTURE

Business Partner (BP 1000001)
│
├── 📍 Addresses (can have multiple)
│   ├── 📧 Emails (multiple per address)
│   ├── 📞 Phones (multiple per address)
│   └── 📠 Fax (multiple per address)
│
├── 🏦 Bank Details
│   └── Account, Bank Key, IBAN
│
├── 🛒 Customer Role
│   ├── Company Code Data (FI)
│   │   └── Payment Terms, Reconciliation Account
│   └── Sales Area Data (SD)
│       └── Pricing, Shipping, Incoterms
│
└── 🏭 Supplier Role (if also a vendor)
    └── Purchasing Organization Data
```


---

## 💼 For SAP Functional Consultants

### How This Helps Your Work

#### 1. **Requirements Gathering**

Use this schema to:
- ✅ Identify available standard fields vs. custom requirements
- ✅ Map business requirements to technical fields
- ✅ Understand SAP's out-of-the-box capabilities
- ✅ Determine gaps requiring customization

#### 2. **Data Migration Planning**

When migrating from legacy systems:

```
Step 1: Review Source Data Fields
Step 2: Map to SAP Fields (using this schema)
Step 3: Identify Transformations Needed
Step 4: Document Field Mappings
Step 5: Plan Validation Rules
```

**Example Mapping**:

| Legacy System | SAP Field (This Schema) | Transformation |
|---------------|-------------------------|----------------|
| CUST_ID | BusinessPartner | Pad with zeros to 10 chars |
| EMAIL_ADDR | EmailAddress | Validate format (max 241 chars) |
| PHONE | PhoneNumber | Split country code and number |

#### 3. **Interface Design**

For custom transactions or Fiori apps:

- 📋 **Field Layouts**: Know which fields belong together
- 🔍 **Search Help**: Understand value lists and dependencies
- ✅ **Validations**: Implement same rules as standard
- 🏷️ **Labels**: Use SAP-standard field descriptions

#### 4. **SAP Table Mappings (Classic to OData)**

Functional consultants often work with transparent tables. Here is how the API entities map to the underlying SAP S/4HANA database:

| OData Entity | SAP Table | Description |
|--------------|-----------|-------------|
| `A_BusinessPartner` | `BUT000` | BP General Data |
| `A_BusinessPartnerAddress` | `BUT020` / `ADRC` | BP Address Links / Master |
| `A_BusinessPartnerBank` | `BUT0BK` | BP Bank Details |
| `A_Customer` | `KNA1` | Customer Master |
| `A_CustomerSalesArea` | `KNVV` | Customer Sales Data |
| `A_Supplier` | `LFA1` | Supplier Master |
| `A_SupplierPurchasingOrg` | `LFM1` | Supplier Purchasing Data |

#### 5. **Configuration (IMG) Dependencies**

Before the API can successfully create records, the following SPRO configurations must be aligned:

1.  **Cross-Application Components**:
    *   `Business Partner -> Basic Settings -> Number Ranges and Groupings`
    *   `Business Partner -> Basic Settings -> Business Partner Roles`
2.  **Master Data Synchronization (CVI)**:
    *   `Cross-Application Components -> Master Data Synchronization -> Customer/Vendor Integration` (Crucial for linking BP to Customer/Supplier).

#### 6. **Business Process Mapping**

### Master Data Management

```
Business Partner Creation
├── Basic Data (A_BusinessPartnerType)
│   ├── BP Number
│   ├── BP Category (Person/Organization)
│   └── BP Grouping
├── Role Assignment (A_BusinessPartnerRoleType)
│   ├── Customer Role
│   └── Supplier Role
├── Address (A_BusinessPartnerAddressType)
│   ├── Street Address
│   ├── City, Postal Code
│   └── Country
└── Contact Information
    ├── Email (A_AddressEmailAddressType)
    ├── Phone (A_AddressPhoneNumberType)
    └── Fax (A_AddressFaxNumberType)
```

### Customer Management

```
Customer Master
├── General Data (A_CustomerType)
├── Company Code Data (A_CustomerCompanyType)
│   ├── Payment Terms
│   ├── Dunning Procedures
│   └── Account Groups
└── Sales Area Data (A_CustomerSalesAreaType)
    ├── Pricing
    ├── Shipping Conditions
    └── Terms of Payment
```

### Supplier Management

```
Supplier Master
├── General Data (A_SupplierType)
├── Company Code Data (A_SupplierCompanyType)
│   ├── Payment Terms
│   ├── Reconciliation Account
│   └── Bank Details
└── Purchasing Organization (A_SupplierPurchasingOrgType)
    ├── Order Currency
    ├── Terms of Payment
    └── Incoterms
```

#### 5. **Training Materials**

Create accurate training documents:

- ✅ Field-by-field descriptions (from `sap:label` and `sap:quickinfo`)
- ✅ Mandatory vs. optional fields (from `Nullable`)
- ✅ Field length limits (from `MaxLength`)
- ✅ Relationships between data (from `NavigationProperties`)

#### 6. **Test Case Development**

Use the schema to create comprehensive test scenarios:

```
Test Case: Create New Business Partner
├── Positive Tests
│   ├── Minimum required fields
│   ├── All fields populated
│   └── Maximum length values
└── Negative Tests
    ├── Missing required fields
    ├── Exceeding max length
    └── Invalid data formats
```

### Key Entity Types for Functional Consultants

| Entity Type | Business Area | Key Fields |
|-------------|---------------|------------|
| `A_BusinessPartnerType` | Master Data | BusinessPartner, BusinessPartnerName, BusinessPartnerCategory |
| `A_CustomerType` | Sales | Customer, CustomerName, CustomerAccountGroup |
| `A_SupplierType` | Procurement | Supplier, SupplierName, SupplierAccountGroup |
| `A_BusinessPartnerAddressType` | Master Data | AddressID, StreetName, CityName, Country |
| `A_CustomerSalesAreaType` | Sales | Customer, SalesOrganization, DistributionChannel, Division |
| `A_SupplierPurchasingOrgType` | Procurement | Supplier, PurchasingOrganization, PurchasingGroup |
| `A_BPContactToAddressType` | Contact Management | ContactPerson, RelationshipNumber, Department |

---

## 💻 For SAP Technical Developers

### Technical Architecture

#### 1. **Authentication Patterns**

Standard S/4HANA OData services support multiple authentication methods. Choose based on your environment:

*   **OAuth 2.0 (Recommended)**: Best for cloud-to-on-premise or external app integration.
*   **SAML 2.0**: Preferred for Single Sign-On (SSO) in corporate environments.
*   **X.509 Client Certificates**: High-security machine-to-machine communication.
*   **Basic Authentication**: Only for development/sandboxes (requires HTTPS).

#### 2. **Security & Authorization Objects**

Access to Business Partner data via API is controlled by the same authorization objects as the `BP` transaction:

| Object | Description | Key Fields |
|--------|-------------|------------|
| `B_BUPA_GRP` | BP: Authorization Groups | `BEGRU` (Auth Group) |
| `B_BUPA_RLT` | BP: BP Roles | `RLTYP` (BP Role) |
| `B_BUPA_ATT` | BP: Auth. Types | `AUTTY` (Auth. Type) |

#### 3. **Extensibility & Custom Fields**

To add custom fields (Z-fields) to this API, follow these steps:

1.  **Append Structure**: Add fields to the relevant BP table (e.g., `BUT000`).
2.  **Customizing**: Enable the fields in the BP Field Grouping configuration.
3.  **BAdI Implementation**: Use BAdI `MD_BUPA_ODATA_CUSTOM_FIELDS` to map custom fields to the OData entity.
4.  **Gateway Service**: If needed, redefine the service in `SEGW` to include the new fields in the metadata.

#### 4. **Schema Structure**

```json
{
  "Namespace": "API_BUSINESS_PARTNER",
  "EntityTypes": [36 entity definitions],
  "Associations": [42 relationships],
  "EntityContainer": {
    "EntitySets": [36 collections],
    "AssociationSets": [42 navigation paths],
    "FunctionImports": [service operations]
  }
}
```

---

## 🧬 Deep Entity Operations (Advanced)

Deep entity operations allow you to create a Business Partner along with all its related child entities (addresses, roles, customer data, etc.) in a **single API call**. This is a powerful feature for reducing network overhead and ensuring transactional consistency.

### Deep POST (Create with Nested Entities)

Instead of making 5+ separate API calls, you can create everything at once:

```json
POST /sap/opu/odata/sap/API_BUSINESS_PARTNER/A_BusinessPartner
Content-Type: application/json

{
  "BusinessPartnerCategory": "2",
  "BusinessPartnerGrouping": "BP01",
  "OrganizationBPName1": "ACME Corporation",
  "SearchTerm1": "ACME",
  "Language": "EN",
  
  "to_BusinessPartnerRole": [
    {
      "BusinessPartnerRole": "FLCU00"
    },
    {
      "BusinessPartnerRole": "FLCU01"
    }
  ],
  
  "to_BusinessPartnerAddress": [
    {
      "Country": "US",
      "CityName": "New York",
      "PostalCode": "10001",
      "StreetName": "5th Avenue",
      "HouseNumber": "123",
      "Language": "EN",
      
      "to_EmailAddress": [
        {
          "EmailAddress": "contact@acme.com",
          "IsDefaultEmailAddress": true
        }
      ],
      "to_PhoneNumber": [
        {
          "PhoneNumber": "+1-212-555-1234",
          "IsDefaultPhoneNumber": true
        }
      ]
    }
  ],
  
  "to_BusinessPartnerBank": [
    {
      "BankCountryKey": "US",
      "BankNumber": "021000021",
      "BankAccount": "123456789",
      "BankAccountHolderName": "ACME Corporation"
    }
  ],
  
  "to_Customer": {
    "CustomerAccountGroup": "KUNA",
    "AuthorizationGroup": "",
    
    "to_CustomerCompany": [
      {
        "CompanyCode": "1000",
        "ReconciliationAccount": "140000",
        "PaymentTerms": "0001"
      }
    ],
    
    "to_CustomerSalesArea": [
      {
        "SalesOrganization": "1000",
        "DistributionChannel": "10",
        "Division": "00",
        "PaymentTerms": "0001",
        "ShippingCondition": "01",
        "IncotermsClassification": "FOB"
      }
    ]
  }
}
```

### Deep Entity Limitations

> [!WARNING]
> **Deep PATCH/PUT is NOT supported** by the standard SAP Gateway framework. For updates, you must call each entity separately.

| Operation | Supported? | Notes |
|-----------|:----------:|-------|
| Deep POST (Create) | ✅ Yes | Create parent + all children in one call |
| Deep GET ($expand) | ✅ Yes | Retrieve related entities together |
| Deep PATCH (Update) | ❌ No | Must update each entity separately |
| Deep DELETE | ❌ No | Must delete children first, then parent |

---

## 🏷️ Complete BP Roles & Categories Reference

Business Partner Roles define **what function** a BP serves in your organization. These are critical for proper system behavior.

### Business Partner Categories

Every BP belongs to exactly **one** category (cannot be changed after creation):

| Category Code | Name | Description | Examples |
|:-------------:|------|-------------|----------|
| **1** | Person | A natural individual | Employee, Contact Person, Private Customer |
| **2** | Organization | A legal entity or company | Company, Department, Association |
| **3** | Group | A collective of persons | Married Couple, Community, Household |

### Standard Business Partner Roles

| Role Code | Role Name | Role Category | Description | Module |
|-----------|-----------|---------------|-------------|--------|
| **000000** | Business Partner (General) | `BUS_PARTNER` | Base role for all BPs | Central |
| **BUP001** | Contact Person | Contact | Person linked to an organization | Central |
| **BUP002** | Portal Provider | Portal | For portal-based scenarios | Portal |
| **BUP003** | Plant | Plant | Plant-specific BP data | MM |
| **FLCU00** | FI Customer | Customer | Customer for Financial Accounting (company code level) | FI |
| **FLCU01** | SD Customer | Customer | Customer for Sales & Distribution (sales area level) | SD |
| **FLVN00** | FI Vendor | Vendor | Supplier for Financial Accounting | FI |
| **FLVN01** | MM Vendor | Vendor | Supplier for Materials Management (purchasing org level) | MM |
| **FS0000** | Bank | FS | Financial Services bank partner | FS |
| **FS0001** | Contract Partner | FS | Contract-based relationship | FS |

### Role Assignment via API

```json
// Assign Customer role (both FI and SD)
POST /A_BusinessPartnerRole
{
  "BusinessPartner": "1000000",
  "BusinessPartnerRole": "FLCU00"  // FI Customer
}

POST /A_BusinessPartnerRole
{
  "BusinessPartner": "1000000",
  "BusinessPartnerRole": "FLCU01"  // SD Customer
}
```

> [!IMPORTANT]
> Assigning `FLCU00` alone will create the customer in FI but will **not** enable sales area data. You need **both** `FLCU00` and `FLCU01` for a complete Sales customer.

---

## 🔄 CVI - Customer/Vendor Integration

In SAP S/4HANA, the **Business Partner** is the leading object. The legacy Customer (`KNA1`) and Vendor (`LFA1`) records are created automatically through the **CVI (Customer/Vendor Integration)** framework.

### How CVI Works

```
┌──────────────────────────────────────────────────────────────┐
│                    CREATE via API                            │
│              A_BusinessPartner + Roles                       │
└───────────────────────┬──────────────────────────────────────┘
                        │
                        ▼
┌──────────────────────────────────────────────────────────────┐
│               SAP CVI Framework                              │
│   (Automatic Synchronization Engine)                         │
└───────────────────────┬──────────────────────────────────────┘
                        │
            ┌───────────┴───────────┐
            ▼                       ▼
┌───────────────────┐   ┌───────────────────┐
│  Customer Tables  │   │  Supplier Tables  │
│  KNA1, KNVV, KNB1 │   │  LFA1, LFM1, LFB1 │
│  (Auto-created)   │   │  (Auto-created)   │
└───────────────────┘   └───────────────────┘
```

### CVI Configuration (SPRO)

Functional consultants must ensure these IMG settings are correct:

| IMG Path | Purpose |
|----------|--------|
| `Cross-Application Components → Master Data Synchronization → Customer/Vendor Integration → Business Partner Settings → Settings for Customer Integration` | Define which BP Grouping creates which Customer Account Group |
| `... → Settings for Vendor Integration` | Define which BP Grouping creates which Supplier Account Group |
| `... → Field Mapping for Customer Integration` | Map BP fields to Customer fields |
| `... → Field Mapping for Vendor Integration` | Map BP fields to Supplier fields |
| `... → Number Assignment` | Define number range synchronization |

### CVI Synchronization Modes

| Mode | Description | When to Use |
|------|-------------|-------------|
| **Synchronous** | Customer/Vendor created immediately when BP is saved | Real-time integration needs |
| **Asynchronous** | Customer/Vendor created via background job | High-volume migration scenarios |

### Common CVI Errors

| Error | Cause | Solution |
|-------|-------|----------|
| `BP_CVI: No assignment found` | BP Grouping not linked to Account Group | Configure in SPRO under CVI settings |
| `Number range not defined` | Missing internal/external number range | Define number ranges in SPRO |
| `Field mapping missing` | Required field not mapped between BP and Customer/Vendor | Add field mapping in CVI configuration |

### CVI Verification Transactions

Before going live, use these transactions to verify CVI setup:

| Transaction | Purpose |
|-------------|---------|
| `MDS_LOAD_COCKPIT` | Synchronization Cockpit - bulk sync BP ↔ Customer/Vendor |
| `CVI_PERIOD_TO_HK` | Master Data Consistency Check |
| `BPCVI_MDCHK` | CVI Customizing Check |
| `CVI_CONT` | CVI Completeness Check |
| `/IWFND/ERROR_LOG` | OData Gateway Error Log |

---

## 🔢 Number Range Configuration

Number ranges determine how Business Partner IDs are generated.

### Configuration Path (SPRO)
```
Cross-Application Components → SAP Business Partner → Business Partner 
  → Basic Settings → Number Ranges and Groupings → Define Number Ranges
```

**Transaction**: `BUCF` (Define Number Ranges for Business Partners)

### Number Range Types

| Type | Description | Example | Use Case |
|------|-------------|---------|----------|
| **Internal** | System auto-generates ID | 1000000001, 1000000002... | Standard customers |
| **External** | User/API provides ID | CUST001, VND-123 | Legacy migrations |

### Grouping and Number Range Assignment

```
                    ┌─────────────────────────────────────┐
                    │         BP Grouping                 │
                    │   (e.g., 'BPCU' = BP Customer)      │
                    └───────────────┬─────────────────────┘
                                    │
                                    ▼
                    ┌─────────────────────────────────────┐
                    │       Number Range Object           │
                    │   (e.g., 'BP_CUS' = 01-19999999)    │
                    └───────────────┬─────────────────────┘
                                    │
          ┌─────────────────────────┴─────────────────────────┐
          ▼                                                   ▼
┌───────────────────┐                               ┌───────────────────┐
│ Internal Interval │                               │ External Interval │
│  01 - 09999999    │                               │  A0000001-ZZZZZZZZ│
│  (Auto-assigned)  │                               │  (User-provided)  │
└───────────────────┘                               └───────────────────┘
```

---

## 📋 Field Groupings & Required Fields

Field visibility and required status can be controlled per BP Role using **Field Groupings**.

### Configuration Path (SPRO)
```
Cross-Application Components → SAP Business Partner → Business Partner
  → Basic Settings → Field Groupings → Configure Field Attributes per BP Role
```

### Field Status Options

| Status | Behavior | API Impact |
|--------|----------|------------|
| **Required** | Must be provided | API returns 400 if missing |
| **Optional** | Can be left empty | No validation |
| **Hidden** | Not visible in UI | Still accessible via API |
| **Display Only** | Read-only in UI | API can still write |

### API-Level Field Detection

```javascript
// Detect required fields from metadata
const metadata = await fetch(`${API_URL}/$metadata`);
// Check for Nullable="false" in EDMX response
// Fields with Nullable="false" are required at API level
```

---

## ✅ Validation Rules (BRFplus)

SAP uses **Business Rule Framework plus (BRFplus)** for data quality validation.

### Managing Validation Rules

**Fiori App**: `Manage Business Partner Validation Rules`

**Common Validation Scenarios**:
- Duplicate detection
- Tax number format validation
- Address completeness checks
- Industry-specific requirements

### Creating Custom Validation (Technical)

```abap
" BRFplus Function example for BP validation
CLASS zcl_bp_validation DEFINITION.
  PUBLIC SECTION.
    METHODS validate_tax_number
      IMPORTING iv_tax_number TYPE bptaxnum
      RETURNING VALUE(rv_valid) TYPE abap_bool.
ENDCLASS.

CLASS zcl_bp_validation IMPLEMENTATION.
  METHOD validate_tax_number.
    " Custom tax number validation logic
    IF iv_tax_number IS INITIAL.
      rv_valid = abap_false.
      RETURN.
    ENDIF.
    " Country-specific format checks
    rv_valid = abap_true.
  ENDMETHOD.
ENDCLASS.
```

---

## 🚨 HTTP Error Codes Reference

Complete reference for API error troubleshooting:

### 400 Bad Request

| Error Message | Cause | Solution |
|---------------|-------|----------|
| `Malformed request syntax` | Invalid JSON payload | Validate JSON structure |
| `Property X is not nullable` | Required field missing | Include all required fields |
| `Value exceeds MaxLength` | Field too long | Check `MaxLength` in schema |
| `Invalid date format` | Wrong date encoding | Use `/Date(timestamp)/` format |
| `Unknown property X` | Field doesn't exist | Check entity schema |

### 404 Not Found

| Error Message | Cause | Solution |
|---------------|-------|----------|
| `Resource not found` | Invalid BP ID | Verify ID exists |
| `Entity set not found` | Wrong entity name | Check `$metadata` for names |
| `Service not active` | OData service deactivated | Activate in `/IWFND/MAINT_SERVICE` |

### 409 Conflict

| Error Message | Cause | Solution |
|---------------|-------|----------|
| `Duplicate key` | ID already exists | Use different ID or PATCH |
| `ETag mismatch` | Concurrent modification | Re-fetch and retry |
| `Optimistic lock failed` | Record changed | Reload current version |

### 500 Internal Server Error

| Common Causes | Diagnostic Steps |
|---------------|------------------|
| Backend exception | Check `/IWFND/ERROR_LOG` |
| Timeout | Reduce batch size (max 100) |
| Missing authorization | Verify user authorizations |
| ABAP dump | Check `ST22` for short dumps |

### Error Response Structure

```json
{
  "error": {
    "code": "BP/001",
    "message": {
      "lang": "en",
      "value": "Business Partner 9999999999 does not exist"
    },
    "innererror": {
      "application": { "component_id": "BP-MD" },
      "transactionid": "A1B2C3D4E5F6",
      "errordetails": [
        { "code": "BP/001", "message": "Business Partner not found" }
      ]
    }
  }
}
```

---

## ⚡ OData Performance Best Practices

Optimize your API calls for production workloads:

### Query Optimization

| Practice | Bad Example | Good Example |
|----------|-------------|--------------|
| Use $select | `GET /A_BusinessPartner` | `GET /A_BusinessPartner?$select=BusinessPartner,BusinessPartnerName` |
| Filter early | `GET /A_Customer` | `GET /A_Customer?$filter=CustomerAccountGroup eq 'KUNA'` |
| Avoid deep $expand | `?$expand=to_A/to_B/to_C/to_D` | Fetch related data separately |
| Use $top/$skip | No pagination | `?$top=100&$skip=0` |

### Batch Request Limits

| Scenario | Recommendation |
|----------|----------------|
| Standard operations | Max 100 per $batch |
| Complex deep inserts | Max 50 per $batch |
| Read operations | Max 200 per $batch |
| Parallel batches | Max 5 concurrent |

### Indexed Fields for Filtering

These fields have database indexes for optimal `$filter` performance:

| Entity | Indexed Fields |
|--------|----------------|
| `A_BusinessPartner` | `BusinessPartner`, `BusinessPartnerCategory`, `SearchTerm1` |
| `A_Customer` | `Customer`, `CustomerAccountGroup` |
| `A_Supplier` | `Supplier`, `SupplierAccountGroup` |
| `A_BusinessPartnerAddress` | `BusinessPartner`, `AddressID`, `Country` |


---

## ☁️ SAP S/4HANA Cloud Setup (Communication Scenario)

For **SAP S/4HANA Cloud** (public or private edition), you must configure a **Communication Arrangement** before calling the API.

### Communication Scenario: `SAP_COM_0008`

This is the standard communication scenario for the Business Partner API.

#### Setup Steps:

1. **Create Communication User** (App: `Maintain Communication Users`)
   - Create a technical user with a strong password
   - Note down the User ID

2. **Create Communication System** (App: `Communication Systems`)
   - Define the external system that will call the API
   - Assign the Communication User

3. **Create Communication Arrangement** (App: `Communication Arrangements`)
   - Select Scenario: `SAP_COM_0008` (Business Partner Integration)
   - Assign the Communication System
   - Note down the Service URL provided

#### Resulting Service URL:
```
https://<tenant>.s4hana.cloud.sap/sap/opu/odata/sap/API_BUSINESS_PARTNER
```

#### Authentication for Cloud:
- **OAuth 2.0 Client Credentials** (Recommended)
- Basic Authentication (only if OAuth is not possible)

```javascript
// OAuth 2.0 Token Request Example
const tokenResponse = await fetch('https://<tenant>.authentication.sap.hana.ondemand.com/oauth/token', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Authorization': 'Basic ' + btoa(clientId + ':' + clientSecret)
  },
  body: 'grant_type=client_credentials'
});

const { access_token } = await tokenResponse.json();

// Use token for API calls
const bpResponse = await fetch(`${serviceUrl}/A_BusinessPartner`, {
  headers: {
    'Authorization': `Bearer ${access_token}`,
    'Accept': 'application/json'
  }
});
```

---

### Development Use Cases

#### 1. **API Integration**

**Consuming the API**:

```javascript
// Example: Fetch Business Partner
GET /sap/opu/odata/sap/API_BUSINESS_PARTNER/A_BusinessPartner('1000000')

Response:
{
  "BusinessPartner": "1000000",
  "Customer": "1000000",
  "Supplier": "",
  "BusinessPartnerCategory": "2",
  "BusinessPartnerFullName": "SAP Industries Corp",
  "BusinessPartnerName": "SAP Industries",
  "CreationDate": "/Date(1609459200000)/",
  "to_BusinessPartnerAddress": {
    "__deferred": {
      "uri": ".../A_BusinessPartner('1000000')/to_BusinessPartnerAddress"
    }
  }
}
```

**Creating Records**:

```javascript
// Example: Create Email Address
POST /sap/opu/odata/sap/API_BUSINESS_PARTNER/A_AddressEmailAddress

Request Body:
{
  "AddressID": "0000012345",
  "Person": "0000000001",
  "OrdinalNumber": "001",
  "IsDefaultEmailAddress": true,
  "EmailAddress": "contact@example.com"
}
```

#### 2. **Database Schema Generation**

Map Entity Types to database tables:

```sql
-- Generated from A_BusinessPartnerType
CREATE TABLE BUSINESS_PARTNER (
  BUSINESS_PARTNER VARCHAR2(10) PRIMARY KEY NOT NULL,
  CUSTOMER VARCHAR2(10),
  SUPPLIER VARCHAR2(10),
  BP_CATEGORY VARCHAR2(1),
  BP_GROUPING VARCHAR2(4),
  BP_NAME VARCHAR2(80),
  BP_FULL_NAME VARCHAR2(81),
  CREATION_DATE DATE,
  CREATED_BY_USER VARCHAR2(12),
  LAST_CHANGE_DATE DATE,
  LAST_CHANGED_BY_USER VARCHAR2(12),
  IS_MARKED_FOR_ARCHIVING NUMBER(1),
  BUSINESS_PARTNER_ID_BY_EXT_SYS VARCHAR2(20)
  -- ... additional fields
);

-- Indexes
CREATE INDEX IDX_BP_CUSTOMER ON BUSINESS_PARTNER(CUSTOMER);
CREATE INDEX IDX_BP_SUPPLIER ON BUSINESS_PARTNER(SUPPLIER);
CREATE INDEX IDX_BP_NAME ON BUSINESS_PARTNER(BP_NAME);
```

#### 3. **Data Model Generation**

**TypeScript/JavaScript**:

```typescript
// Generated from schema
interface BusinessPartner {
  BusinessPartner: string;  // Required, max 10 chars
  Customer?: string;        // Optional, max 10 chars
  Supplier?: string;        // Optional, max 10 chars
  BusinessPartnerCategory?: string;  // max 1 char
  BusinessPartnerGrouping?: string;  // max 4 chars
  BusinessPartnerName?: string;      // max 80 chars
  BusinessPartnerFullName?: string;  // max 81 chars
  CreationDate?: Date;
  CreatedByUser?: string;   // max 12 chars
  LastChangeDate?: Date;
  LastChangedByUser?: string;  // max 12 chars
  IsMarkedForArchiving?: boolean;
  // Navigation properties
  to_BusinessPartnerAddress?: BusinessPartnerAddress[];
  to_BusinessPartnerBank?: BusinessPartnerBank[];
  to_BusinessPartnerContact?: BusinessPartnerContact[];
  to_BusinessPartnerRole?: BusinessPartnerRole[];
}

interface AddressEmailAddress {
  AddressID: string;        // Required, max 10 chars
  Person: string;           // Required, max 10 chars
  OrdinalNumber: string;    // Required, max 3 chars
  IsDefaultEmailAddress?: boolean;
  EmailAddress?: string;    // max 241 chars
  SearchEmailAddress?: string;  // max 20 chars
  AddressCommunicationRemarkText?: string;  // max 50 chars
}
```

**Java/POJO**:

```java
// Generated from schema
@Entity
@Table(name = "BUSINESS_PARTNER")
public class BusinessPartner {
    
    @Id
    @Column(name = "BUSINESS_PARTNER", length = 10, nullable = false)
    private String businessPartner;
    
    @Column(name = "CUSTOMER", length = 10)
    private String customer;
    
    @Column(name = "SUPPLIER", length = 10)
    private String supplier;
    
    @Column(name = "BP_CATEGORY", length = 1)
    private String businessPartnerCategory;
    
    @Column(name = "BP_NAME", length = 80)
    private String businessPartnerName;
    
    @Temporal(TemporalType.DATE)
    @Column(name = "CREATION_DATE")
    private Date creationDate;
    
    @OneToMany(mappedBy = "businessPartner")
    private List<BusinessPartnerAddress> addresses;
    
    @OneToMany(mappedBy = "businessPartner")
    private List<BusinessPartnerRole> roles;
    
    // Getters and setters
}
```

**Python/Dataclass**:

```python
from dataclasses import dataclass
from typing import Optional, List
from datetime import date

@dataclass
class BusinessPartner:
    BusinessPartner: str  # max_length=10, required
    Customer: Optional[str] = None  # max_length=10
    Supplier: Optional[str] = None  # max_length=10
    BusinessPartnerCategory: Optional[str] = None  # max_length=1
    BusinessPartnerGrouping: Optional[str] = None  # max_length=4
    BusinessPartnerName: Optional[str] = None  # max_length=80
    BusinessPartnerFullName: Optional[str] = None  # max_length=81
    CreationDate: Optional[date] = None
    CreatedByUser: Optional[str] = None  # max_length=12
    LastChangeDate: Optional[date] = None
    LastChangedByUser: Optional[str] = None  # max_length=12
    IsMarkedForArchiving: Optional[bool] = None
    
    # Validation
    def __post_init__(self):
        if len(self.BusinessPartner) > 10:
            raise ValueError("BusinessPartner exceeds maximum length of 10")
```

#### 4. **Validation Framework**

```python
# Example validation using schema
class BusinessPartnerValidator:
    
    def __init__(self, schema_path):
        with open(schema_path, 'r') as f:
            self.schema = json.load(f)
        self.entity_types = {
            et['Name']: et for et in self.schema['EntityTypes']
        }
    
    def validate_entity(self, entity_type_name, data):
        entity_def = self.entity_types.get(entity_type_name)
        if not entity_def:
            raise ValueError(f"Unknown entity type: {entity_type_name}")
        
        errors = []
        
        # Validate required fields
        for key_field in entity_def.get('Key', []):
            if key_field not in data:
                errors.append(f"Missing required field: {key_field}")
        
        # Validate properties
        for prop in entity_def.get('Properties', []):
            prop_name = prop['Name']
            if prop_name in data:
                value = data[prop_name]
                
                # Check nullable
                if not prop.get('Nullable', True) and value is None:
                    errors.append(f"{prop_name} cannot be null")
                
                # Check max length
                if 'MaxLength' in prop and isinstance(value, str):
                    if len(value) > prop['MaxLength']:
                        errors.append(
                            f"{prop_name} exceeds max length "
                            f"({len(value)} > {prop['MaxLength']})"
                        )
                
                # Check type
                expected_type = prop['Type']
                if not self._validate_type(value, expected_type):
                    errors.append(
                        f"{prop_name} has wrong type "
                        f"(expected {expected_type})"
                    )
        
        return errors if errors else None
```

#### 5. **API Client Generation**

```typescript
// Auto-generated API client with production-ready error handling
interface ApiError {
  code: string;
  message: string;
  details?: string[];
}

class BusinessPartnerApiError extends Error {
  constructor(public statusCode: number, public apiError: ApiError) {
    super(apiError.message);
    this.name = 'BusinessPartnerApiError';
  }
}

class BusinessPartnerAPI {
  private baseUrl: string;
  private csrfToken: string | null = null;
  
  constructor(baseUrl: string) {
    this.baseUrl = baseUrl;
  }
  
  // Fetch CSRF token for write operations
  private async fetchCsrfToken(): Promise<string> {
    const response = await fetch(`${this.baseUrl}/A_BusinessPartner`, {
      method: 'HEAD',
      headers: { 'X-CSRF-Token': 'Fetch' }
    });
    const token = response.headers.get('X-CSRF-Token');
    if (!token) {
      throw new Error('Failed to fetch CSRF token');
    }
    this.csrfToken = token;
    return token;
  }
  
  // Generic response handler with error checking
  private async handleResponse<T>(response: Response): Promise<T> {
    if (!response.ok) {
      const errorBody = await response.json().catch(() => ({}));
      throw new BusinessPartnerApiError(response.status, {
        code: errorBody?.error?.code || `HTTP_${response.status}`,
        message: errorBody?.error?.message?.value || response.statusText,
        details: errorBody?.error?.innererror?.errordetails?.map((e: any) => e.message)
      });
    }
    return response.json();
  }
  
  // Get Business Partner with error handling
  async getBusinessPartner(id: string): Promise<BusinessPartner> {
    const response = await fetch(
      `${this.baseUrl}/A_BusinessPartner('${encodeURIComponent(id)}')`,
      { headers: { 'Accept': 'application/json' } }
    );
    const data = await this.handleResponse<{ d: BusinessPartner }>(response);
    return data.d;
  }
  
  // Create Business Partner with CSRF token
  async createBusinessPartner(data: BusinessPartner): Promise<BusinessPartner> {
    if (!this.csrfToken) {
      await this.fetchCsrfToken();
    }
    
    const response = await fetch(
      `${this.baseUrl}/A_BusinessPartner`,
      {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'Accept': 'application/json',
          'X-CSRF-Token': this.csrfToken!
        },
        body: JSON.stringify(data)
      }
    );
    const result = await this.handleResponse<{ d: BusinessPartner }>(response);
    return result.d;
  }
  
  // Update Business Partner with optimistic locking
  async updateBusinessPartner(
    id: string,
    data: Partial<BusinessPartner>,
    etag: string = '*'
  ): Promise<void> {
    if (!this.csrfToken) {
      await this.fetchCsrfToken();
    }
    
    const response = await fetch(
      `${this.baseUrl}/A_BusinessPartner('${encodeURIComponent(id)}')`,
      {
        method: 'PATCH',
        headers: {
          'Content-Type': 'application/json',
          'X-CSRF-Token': this.csrfToken!,
          'If-Match': etag
        },
        body: JSON.stringify(data)
      }
    );
    
    if (!response.ok) {
      await this.handleResponse(response);
    }
  }
  
  // Get addresses with proper response parsing
  async getBusinessPartnerAddresses(
    id: string
  ): Promise<BusinessPartnerAddress[]> {
    const response = await fetch(
      `${this.baseUrl}/A_BusinessPartner('${encodeURIComponent(id)}')/to_BusinessPartnerAddress`,
      { headers: { 'Accept': 'application/json' } }
    );
    const data = await this.handleResponse<{ d: { results: BusinessPartnerAddress[] } }>(response);
    return data.d.results;
  }
}
```


#### 6. **GraphQL Schema Generation**

```graphql
# ... GraphQL content ...
```

---

## 🚀 Scalability & Best Practices

For enterprise-grade integrations handling millions of records, follow these scalability patterns:

### 1. **Batch Processing ($batch)**
Never update 1,000 records with 1,000 individual HTTP calls. Use OData Batching to group up to 100 operations per request to reduce network overhead.

### 2. **Delta Loads**
Use the `ChangedOn` or `LastChangeDate` filters to only fetch records modified since your last sync.
`GET /A_BusinessPartner?$filter=LastChangeDate gt datetime'2026-01-01T00:00:00'`

### 3. **Server-Side Paging**
The API supports `$top` and `$skip`. Always implement paging to avoid timeouts on large datasets.
`GET /A_BusinessPartner?$top=100&$skip=500`

### 4. **Avoid Deep Expands**
While `$expand=to_BusinessPartnerAddress/to_EmailAddress` is convenient, deep nesting can lead to performance degradation on the SAP Gateway layer. Limit expands to 2 levels where possible.

### 5. **Error Handling & Retry Logic**
SAP returns detailed error messages in the `error` object. Implement exponential backoff for `503 Service Unavailable` or `429 Too Many Requests` (if using SAP Cloud Integration).

---

## 🛠️ Developer Tools & Assets

### 📮 Postman Collection
We have provided a sample Postman collection in the repository: [Postman_Collection.json](file:///Users/techsavvy/Downloads/Ultimate-Guide-For-SAP-OData-API_BUSINESS_PARTNER/Postman_Collection.json) to jumpstart your testing.

### 🏗️ Code Generators
Use the [SAP Cloud SDK](https://sdk.sap.com/) to automatically generate type-safe clients for TypeScript or Java directly from the `API_BUSINESS_PARTNER_SCHEMA.json` provided here.

---

### Technical Specifications

#### Data Types Mapping

| OData Type | JSON Type | Java Type | TypeScript Type | SQL Type |
|------------|-----------|-----------|-----------------|----------|
| Edm.String | string | String | string | VARCHAR |
| Edm.Boolean | boolean | Boolean | boolean | BIT/BOOLEAN |
| Edm.DateTime | string (ISO) | Date | Date | DATETIME |
| Edm.DateTimeOffset | string (ISO) | OffsetDateTime | Date | TIMESTAMP |
| Edm.Decimal | number | BigDecimal | number | DECIMAL |
| Edm.Int16 | number | Short | number | SMALLINT |
| Edm.Time | string | LocalTime | string | TIME |
| Edm.Guid | string | UUID | string | CHAR(36) |

#### Navigation Patterns

```
Business Partner (1) ──→ (0..*) Addresses
Business Partner (1) ──→ (0..*) Roles
Business Partner (1) ──→ (0..*) Bank Details
Business Partner (1) ──→ (0..*) Tax Numbers
Business Partner (1) ──→ (0..*) Identifications

Customer (1) ──→ (0..*) Sales Areas
Customer (1) ──→ (0..*) Company Codes
Supplier (1) ──→ (0..*) Purchasing Organizations
Supplier (1) ──→ (0..*) Company Codes

Address (1) ──→ (0..*) Email Addresses
Address (1) ──→ (0..*) Phone Numbers
Address (1) ──→ (0..*) Fax Numbers
Address (1) ──→ (0..*) URLs
```

### Performance Considerations

#### 1. **Selective Field Loading**

```javascript
// Instead of loading all fields
GET /A_BusinessPartner('1000000')

// Load only needed fields
GET /A_BusinessPartner('1000000')?$select=BusinessPartner,BusinessPartnerName,Customer
```

#### 2. **Expand Relationships Efficiently**

```javascript
// Load business partner with addresses in one call
GET /A_BusinessPartner('1000000')?$expand=to_BusinessPartnerAddress

// Multi-level expansion
GET /A_BusinessPartner('1000000')?
  $expand=to_BusinessPartnerAddress/to_EmailAddress
```

#### 3. **Filtering at Source**

```javascript
// Filter on server side
GET /A_BusinessPartner?
  $filter=BusinessPartnerCategory eq '2' and 
          Customer ne null&
  $orderby=BusinessPartnerName
```

#### 4. **Batch Operations**

```javascript
// Process multiple operations in single HTTP request
POST /$batch
Content-Type: multipart/mixed; boundary=batch_123

--batch_123
Content-Type: application/http

GET A_BusinessPartner('1000000') HTTP/1.1

--batch_123
Content-Type: application/http

GET A_Customer('1000000') HTTP/1.1

--batch_123--
```

---

## 📊 Understanding the Data Structure

### Hierarchical View

```
API_BUSINESS_PARTNER (Root Schema)
│
├─ MASTER DATA ENTITIES
│  ├─ Business Partner (Core)
│  │  ├─ General Data
│  │  ├─ Classification
│  │  └─ Central Attributes
│  │
│  ├─ Customer Extension
│  │  ├─ General Data
│  │  ├─ Sales Organization Data
│  │  └─ Company Code Data
│  │
│  └─ Supplier Extension
│     ├─ General Data
│     ├─ Purchasing Organization Data
│     └─ Company Code Data
│
├─ ADDRESS & CONTACT ENTITIES
│  ├─ Business Partner Address
│  ├─ Email Address
│  ├─ Phone Number (Mobile & Landline)
│  ├─ Fax Number
│  └─ Homepage URL
│
├─ RELATIONSHIP ENTITIES
│  ├─ Business Partner Roles
│  ├─ Contact Person Relationships
│  ├─ Address Usages
│  └─ Partner Functions
│
├─ FINANCIAL ENTITIES
│  ├─ Bank Details
│  ├─ Tax Numbers
│  ├─ Payment Terms
│  ├─ Withholding Tax
│  └─ Dunning Data
│
└─ CLASSIFICATION ENTITIES
   ├─ Industry Codes
   ├─ Identifications
   ├─ Tax Grouping
   └─ Address Dependent Info
```

### Entity Relationship Diagram

```
┌─────────────────────┐
│  Business Partner   │ (Central)
│  (1)                │
└──────────┬──────────┘
           │
           ├──→ (0..*) Addresses
           │            │
           │            ├──→ (0..*) Email Addresses
           │            ├──→ (0..*) Phone Numbers
           │            ├──→ (0..*) Fax Numbers
           │            └──→ (0..*) URLs
           │
           ├──→ (0..*) Roles
           │            ├──→ Customer Role
           │            └──→ Supplier Role
           │
           ├──→ (0..*) Bank Details
           ├──→ (0..*) Tax Numbers
           ├──→ (0..*) Identifications
           └──→ (0..*) Contact Persons
                        │
                        └──→ (1) Address
                                 ├──→ Email
                                 ├──→ Phone
                                 └──→ Fax

┌─────────────────────┐
│     Customer        │ (Extends BP)
│     (0..1)          │
└──────────┬──────────┘
           │
           ├──→ (1..*) Sales Areas
           │            ├──→ Tax Info
           │            ├──→ Partner Functions
           │            └──→ Texts
           │
           └──→ (1..*) Company Codes
                        ├──→ Payment Data
                        ├──→ Dunning Data
                        ├──→ Withholding Tax
                        └──→ Texts

┌─────────────────────┐
│     Supplier        │ (Extends BP)
│     (0..1)          │
└──────────┬──────────┘
           │
           ├──→ (1..*) Purchasing Orgs
           │            ├──→ Partner Functions
           │            └──→ Texts
           │
           └──→ (1..*) Company Codes
                        ├──→ Payment Data
                        └──→ Texts
```

---

## 📚 Complete Entity Type Reference

### 1️⃣ Core Master Data (4 Entities)

#### **A_BusinessPartnerType**
**Purpose**: Central master data for any business partner  
**Key**: `BusinessPartner` (10 chars)  
**Properties**: 58 fields

**Key Fields**:
- `BusinessPartner` - Unique ID (10 chars, required)
- `BusinessPartnerCategory` - Person (1) or Organization (2)
- `BusinessPartnerGrouping` - Classification code

**Important Properties**:
- `BusinessPartnerName` - Name (80 chars)
- `BusinessPartnerFullName` - Full name (81 chars)
- `SearchTerm1`, `SearchTerm2` - Search fields
- `CreationDate`, `CreatedByUser` - Audit fields
- `Customer` - Customer number if BP is a customer
- `Supplier` - Supplier number if BP is a supplier

**Navigation**:
- `to_BusinessPartnerAddress` - All addresses
- `to_BusinessPartnerBank` - Bank details
- `to_BusinessPartnerContact` - Contact persons
- `to_BusinessPartnerRole` - Assigned roles
- `to_BusinessPartnerTaxNumber` - Tax numbers

---

#### **A_BusinessPartnerAddressType**
**Purpose**: Address records for business partners  
**Key**: `BusinessPartner` + `AddressID`  
**Properties**: 49 fields

**Key Fields**:
- `BusinessPartner` (10 chars, required)
- `AddressID` (10 chars, required)

**Important Properties**:
- `StreetName`, `HouseNumber`, `AdditionalStreetPrefixName`
- `CityName`, `PostalCode`, `Country`
- `Region` - State/Province
- `Language` - Communication language
- `ValidityStartDate`, `ValidityEndDate`

**Navigation**:
- `to_EmailAddress` - Email addresses for this address
- `to_PhoneNumber` - Phone numbers
- `to_FaxNumber` - Fax numbers
- `to_URLAddress` - Web URLs

---

#### **A_BusinessPartnerBankType**
**Purpose**: Bank account details  
**Key**: `BusinessPartner` + `BankIdentification`  
**Properties**: 22 fields

**Important Properties**:
- `BankCountryKey` - Country of bank
- `BankNumber` - Bank code
- `BankAccount` - Account number
- `BankAccountHolderName` - Account holder
- `BankControlKey` - Check digit
- `IBAN` - International bank account number
- `IBANValidityStartDate`
- `BankAccountReferenceText`

---

#### **A_BusinessPartnerContactType**
**Purpose**: Contact persons linked to business partners  
**Key**: `RelationshipNumber` + `BusinessPartnerCompany` + `BusinessPartnerPerson` + `ValidityEndDate`  
**Properties**: 35 fields

**Important Properties**:
- `RelationshipNumber` (12 chars)
- `BusinessPartnerCompany` - Company BP number
- `BusinessPartnerPerson` - Person BP number
- `ContactPersonFunction` - Job role
- `ContactPersonDepartment`
- `PhoneNumber`, `EmailAddress`
- `RelationshipCategory` - Type of relationship

---

### 2️⃣ Address & Communication (6 Entities)

#### **A_AddressEmailAddressType**
**Purpose**: Email addresses  
**Key**: `AddressID` + `Person` + `OrdinalNumber`  
**Properties**: 7 fields

**Important Properties**:
- `EmailAddress` (max 241 chars)
- `IsDefaultEmailAddress` - Flag for default email
- `SearchEmailAddress` - Search field (20 chars)

---

#### **A_AddressPhoneNumberType**
**Purpose**: Phone numbers (mobile and landline)  
**Key**: `AddressID` + `Person` + `OrdinalNumber`  
**Properties**: 10 fields

**Important Properties**:
- `DestinationLocationCountry` - Country code
- `PhoneNumber` (30 chars) - Number with dialing code
- `PhoneNumberExtension` - Extension (10 chars)
- `InternationalPhoneNumber` - Complete formatted number
- `PhoneNumberType` - Mobile indicator
- `IsDefaultPhoneNumber` - Default flag

---

#### **A_AddressFaxNumberType**
**Purpose**: Fax numbers  
**Key**: `AddressID` + `Person` + `OrdinalNumber`  
**Properties**: 9 fields

**Important Properties**:
- `FaxCountry` - Country code
- `FaxNumber` (30 chars)
- `FaxNumberExtension`
- `InternationalFaxNumber`
- `IsDefaultFaxNumber`

---

#### **A_AddressHomePageURLType**
**Purpose**: Website URLs  
**Key**: `AddressID` + `Person` + `OrdinalNumber` + `ValidityStartDate` + `IsDefaultURLAddress`  
**Properties**: 9 fields

**Important Properties**:
- `WebsiteURL` (max 2048 chars)
- `SearchURLAddress` - Search field
- `URLFieldLength`
- `IsDefaultURLAddress`

---

#### **A_BPContactToAddressType**
**Purpose**: Addresses for contact persons  
**Key**: Composite of 5 fields  
**Properties**: 49 fields

(Similar structure to BusinessPartnerAddress but for contact persons)

---

#### **A_BuPaAddressUsageType**
**Purpose**: Links addresses to specific usage types  
**Key**: `BusinessPartner` + `ValidityEndDate` + `AddressUsage` + `AddressID`  
**Properties**: 8 fields

**Important Properties**:
- `AddressUsage` - Purpose code (e.g., 'XXDEFAULT', 'SHIP-TO')
- `ValidityStartDate`, `ValidityEndDate`
- `StandardUsage` - Default for this usage type

---

### 3️⃣ Customer Entities (7 Entities)

#### **A_CustomerType**
**Purpose**: Customer general data  
**Key**: `Customer`  
**Properties**: 58 fields

**Important Properties**:
- `Customer` (10 chars, required)
- `CustomerName` (80 chars)
- `CustomerAccountGroup` - Classification
- `NIBankAccount` - National bank account
- `SalesOrganization`, `DistributionChannel`, `Division`
- `Industry` - Industry classification
- `TradingPartner` - Related BP

---

#### **A_CustomerCompanyType**
**Purpose**: Customer data per company code  
**Key**: `Customer` + `CompanyCode`  
**Properties**: 44 fields

**Important Properties**:
- `CompanyCode` (4 chars, required)
- `APARToleranceGroup`
- `AccountingClerk`
- `ReconciliationAccount` - G/L account
- `PaymentTerms`
- `PaymentMethodsList`
- `PaymentBlockingReason`
- `CustomerIsBlockedForPosting`

**Navigation**:
- `to_CustomerDunning` - Dunning procedures
- `to_WithHoldingTax` - Tax withholding
- `to_CompanyText` - Long texts

---

#### **A_CustomerSalesAreaType**
**Purpose**: Customer data per sales area  
**Key**: `Customer` + `SalesOrganization` + `DistributionChannel` + `Division`  
**Properties**: 78 fields

**Important Properties**:
- `SalesDistrict`, `SalesOffice`, `SalesGroup`
- `CustomerGroup`, `CustomerPricingProcedure`
- `PriceListType`, `PaymentTerms`
- `DeliveryPriority`, `ShippingCondition`
- `IncotermsClassification`, `IncotermsLocation1`
- `AccountByCustomer` - Payer
- `OrderCombinationIsAllowed`
- `SalesBlocked`, `DeliveryIsBlocked`, `BillingIsBlockedForCustomer`

**Navigation**:
- `to_PartnerFunction` - Partner roles
- `to_SalesAreaTax` - Tax classifications
- `to_UnloadingPoint` - Delivery points
- `to_SalesAreaText` - Long texts

---

#### **A_CustomerSalesAreaTaxType**
**Purpose**: Tax classifications per sales area  
**Key**: `Customer` + `SalesOrganization` + `DistributionChannel` + `Division` + `DepartureCountry` + `CustomerTaxCategory`  
**Properties**: 10 fields

**Important Properties**:
- `DepartureCountry` - Ship-from country
- `CustomerTaxCategory` - Tax category
- `CustomerTaxClassification` - Tax code

---

#### **A_CustomerTaxGroupingType**
**Purpose**: Tax grouping for customer  
**Key**: `Customer` + `CustomerTaxGroupingCode`  
**Properties**: 7 fields

---

#### **A_CustomerUnloadingPointType**
**Purpose**: Unloading points for deliveries  
**Key**: `Customer` + `UnloadingPointName`  
**Properties**: 12 fields

**Important Properties**:
- `UnloadingPointName` (25 chars)
- `CustomerFactory` - Factory calendar
- `BPGoodsReceivingHoursCode` - Receiving hours
- `UnloadingPointAddress`

---

#### **A_CustUnldgPtAddrDepdntInfoType**
**Purpose**: Address-dependent unloading point info  
**Key**: Composite of multiple fields  
**Properties**: 8 fields

---

### 4️⃣ Supplier Entities (4 Entities)

#### **A_SupplierType**
**Purpose**: Supplier general data  
**Key**: `Supplier`  
**Properties**: 50 fields

**Important Properties**:
- `Supplier` (10 chars, required)
- `SupplierName` (80 chars)
- `SupplierAccountGroup`
- `AuthorizationGroup`
- `VATRegistration` - Tax number
- `Industry`
- `PostingIsBlocked`, `PurchasingIsBlocked`, `PaymentIsBlockedForSupplier`

---

#### **A_SupplierCompanyType**
**Purpose**: Supplier data per company code  
**Key**: `Supplier` + `CompanyCode`  
**Properties**: 43 fields

**Important Properties**:
- `CompanyCode` (4 chars, required)
- `ReconciliationAccount`
- `PaymentTerms`
- `PaymentMethodsList`
- `PaymentBlockingReason`
- `WithholdingTaxCountry`
- `SupplierIsBlockedForPosting`

**Navigation**:
- `to_CompanyText` - Long texts

---

#### **A_SupplierPurchasingOrgType**
**Purpose**: Supplier data per purchasing org  
**Key**: `Supplier` + `PurchasingOrganization`  
**Properties**: 42 fields

**Important Properties**:
- `PurchasingOrganization` (4 chars, required)
- `PurchasingGroup`
- `Currency` - Order currency
- `PaymentTerms`
- `IncotermsClassification`, `IncotermsLocation1`
- `PurOrdAutoGenerationIsAllowed`
- `SupplierIsBlockedForPosting`
- `SupplierRespSalesPersonName`

**Navigation**:
- `to_PartnerFunction` - Partner roles
- `to_PurchasingOrgText` - Long texts

---

#### **A_SupplierPartnerFuncType**
**Purpose**: Partner functions for supplier purchasing org  
**Key**: `Supplier` + `PurchasingOrganization` + `SupplierSubrange` + `Plant` + `PartnerFunction` + `PartnerCounter`  
**Properties**: 13 fields

**Important Properties**:
- `PartnerFunction` - Role code (e.g., 'VN' = Vendor)
- `DefaultPartner` - Default flag
- `Supplier` - Partner BP number

---

### 5️⃣ Classification & Identification (6 Entities)

#### **A_BusinessPartnerRoleType**
**Purpose**: Business partner role assignments  
**Key**: `BusinessPartner` + `BusinessPartnerRole`  
**Properties**: 5 fields

**Important Properties**:
- `BusinessPartnerRole` - Role code (e.g., 'FLCU00' = Customer)
- `ValidFrom`, `ValidTo` - Validity period

---

#### **A_BusinessPartnerTaxNumberType**
**Purpose**: Tax numbers and registrations  
**Key**: `BusinessPartner` + `BPTaxType`  
**Properties**: 7 fields

**Important Properties**:
- `BPTaxType` - Tax type (e.g., 'DE1' = VAT number Germany)
- `BPTaxNumber` (20 chars) - Tax ID
- `BPTaxLongNumber` (60 chars) - Extended tax number

---

#### **A_BuPaIdentificationType**
**Purpose**: Identifications and ID numbers  
**Key**: `BusinessPartner` + `BPIdentificationType` + `BPIdentificationNumber`  
**Properties**: 8 fields

**Important Properties**:
- `BPIdentificationType` - ID type code
- `BPIdentificationNumber` (60 chars)
- `BPIdnNmbrIssuingInstitute` - Issuing authority
- `ValidityStartDate`, `ValidityEndDate`

---

#### **A_BuPaIndustryType**
**Purpose**: Industry classifications  
**Key**: `IndustrySector` + `IndustrySystemType` + `BusinessPartner`  
**Properties**: 6 fields

**Important Properties**:
- `IndustrySector` - Industry code
- `IndustrySystemType` - Classification system
- `IsStandardIndustry` - Primary industry flag

---

#### **A_BPContactToFuncAndDeptType**
**Purpose**: Contact person functions and departments  
**Key**: Composite of 6 fields  
**Properties**: 9 fields

**Important Properties**:
- `ContactPersonFunction` (4 chars) - Job function code
- `ContactPersonDepartment` (4 chars) - Department code

---

#### **A_BPAddrDepdntIntlLocNumberType**
**Purpose**: International location numbers per address  
**Key**: `BusinessPartner` + `AddressID` + `InternationalLocationNumber1`  
**Properties**: 4 fields

---

### 6️⃣ Additional Customer Entities (6 Entities)

#### **A_CustomerWithHoldingTaxType**
**Purpose**: Withholding tax codes for customer  
**Key**: `Customer` + `CompanyCode` + `WithholdingTaxType`  
**Properties**: 10 fields

---

#### **A_CustAddrDepdntExtIdentifierType**
**Purpose**: External identifiers per customer address  
**Key**: `Customer` + `AddressID`  
**Properties**: 3 fields

---

#### **A_CustAddrDepdntInformationType**
**Purpose**: Additional info per customer address  
**Key**: `Customer` + `AddressID`  
**Properties**: 6 fields

**Important Properties**:
- `ExpressTrainStationName`
- `TrainStationName`
- `CityCode`
- `County`

---

#### **A_CustomerCompanyTextType**
**Purpose**: Long texts for customer company code  
**Key**: `Customer` + `CompanyCode` + `Language` + `LongTextID`  
**Properties**: 5 fields

---

#### **A_CustomerDunningType**
**Purpose**: Dunning procedures per company code  
**Key**: `Customer` + `CompanyCode` + `DunningArea`  
**Properties**: 12 fields

**Important Properties**:
- `DunningProcedure`
- `DunningLevel`
- `LastDunnedOn`
- `DunningBlockingReason`

---

#### **A_CustomerSalesAreaTextType**
**Purpose**: Long texts for customer sales area  
**Key**: `Customer` + `SalesOrganization` + `DistributionChannel` + `Division` + `Language` + `LongTextID`  
**Properties**: 7 fields

---

### 7️⃣ Additional Supplier Entities (2 Entities)

#### **A_SupplierCompanyTextType**
**Purpose**: Long texts for supplier company code  
**Key**: `Supplier` + `CompanyCode` + `Language` + `LongTextID`  
**Properties**: 5 fields

---

#### **A_SupplierPurchasingOrgTextType**
**Purpose**: Long texts for supplier purchasing org  
**Key**: `Supplier` + `PurchasingOrganization` + `Language` + `LongTextID`  
**Properties**: 5 fields

---

## 🔄 Business Processes Covered

### Process 1: Create New Business Partner

```
Step 1: Create Business Partner Master
├─ Entity: A_BusinessPartnerType
├─ Required: BusinessPartner, Category
└─ Optional: Name, Grouping, Search terms

Step 2: Assign Roles
├─ Entity: A_BusinessPartnerRoleType
├─ Create role: Customer (FLCU00)
└─ Create role: Supplier (FLVN00) if applicable

Step 3: Add Addresses
├─ Entity: A_BusinessPartnerAddressType
├─ Required: AddressID, Country
└─ Optional: Street, City, Postal Code

Step 4: Add Communication Data
├─ Email: A_AddressEmailAddressType
├─ Phone: A_AddressPhoneNumberType
├─ Fax: A_AddressFaxNumberType
└─ URL: A_AddressHomePageURLType

Step 5: Add Financial Data
├─ Bank: A_BusinessPartnerBankType
└─ Tax Numbers: A_BusinessPartnerTaxNumberType

Step 6: Extend to Customer (if applicable)
├─ General: A_CustomerType
├─ Company Code: A_CustomerCompanyType
└─ Sales Area: A_CustomerSalesAreaType

Step 7: Extend to Supplier (if applicable)
├─ General: A_SupplierType
├─ Company Code: A_SupplierCompanyType
└─ Purchasing Org: A_SupplierPurchasingOrgType
```

### Process 2: Maintain Customer Sales Data

```
1. Navigate to Customer → Sales Area
   Entity: A_CustomerSalesAreaType

2. Maintain Basic Sales Data
   ├─ Pricing: Pricing Procedure, Price List
   ├─ Delivery: Shipping Conditions, Delivery Priority
   ├─ Terms: Payment Terms, Incoterms
   └─ Blocks: Sales Block, Delivery Block, Billing Block

3. Assign Partner Functions
   Entity: A_CustomerSalesAreaType → to_PartnerFunction
   ├─ Sold-to Party
   ├─ Ship-to Party
   ├─ Bill-to Party
   └─ Payer

4. Maintain Tax Data
   Entity: A_CustomerSalesAreaTaxType
   └─ Tax Classification per Country

5. Create Unloading Points
   Entity: A_CustomerUnloadingPointType
   └─ Delivery Location Details
```

### Process 3: Vendor Master Creation

```
1. Create Supplier General Data
   Entity: A_SupplierType
   └─ Supplier Number, Name, Account Group

2. Maintain Company Code Data
   Entity: A_SupplierCompanyType
   ├─ Reconciliation Account
   ├─ Payment Terms
   └─ Payment Methods

3. Create Purchasing Organization Data
   Entity: A_SupplierPurchasingOrgType
   ├─ Order Currency
   ├─ Incoterms
   └─ Purchasing Group

4. Assign Partner Functions
   Entity: A_SupplierPartnerFuncType
   └─ Ordering Address, Invoicing Party
```

### Process 4: Contact Person Management

```
1. Create Contact Person as Business Partner
   Entity: A_BusinessPartnerType
   └─ Category = "1" (Person)

2. Link to Company
   Entity: A_BusinessPartnerContactType
   ├─ Relationship to company BP
   ├─ Function and Department
   └─ Validity Period

3. Maintain Contact Address
   Entity: A_BPContactToAddressType
   └─ Address details for contact

4. Add Communication Methods
   ├─ Email: via to_EmailAddress
   ├─ Phone: via to_PhoneNumber
   └─ Mobile: via to_MobilePhoneNumber
```

---

## 🔌 Integration Scenarios

### Scenario 1: Customer Creation from E-Commerce

```javascript
// Step 1: Create Business Partner
POST /A_BusinessPartner
{
  "BusinessPartnerCategory": "2",
  "BusinessPartnerGrouping": "Z001",
  "BusinessPartnerName": "ACME Corporation",
  "SearchTerm1": "ACME"
}

// Step 2: Assign Customer Role
POST /A_BusinessPartnerRole
{
  "BusinessPartner": "1000000",
  "BusinessPartnerRole": "FLCU00"
}

// Step 3: Create Customer Record
POST /A_Customer
{
  "Customer": "1000000",
  "CustomerName": "ACME Corporation",
  "CustomerAccountGroup": "KUNA"
}

// Step 4: Create Sales Area Data
POST /A_CustomerSalesArea
{
  "Customer": "1000000",
  "SalesOrganization": "1000",
  "DistributionChannel": "10",
  "Division": "00",
  "PaymentTerms": "0001",
  "ShippingCondition": "01"
}

// Step 5: Add Address
POST /A_BusinessPartnerAddress
{
  "BusinessPartner": "1000000",
  "Country": "US",
  "CityName": "New York",
  "PostalCode": "10001",
  "StreetName": "5th Avenue",
  "HouseNumber": "123"
}
```

### Scenario 2: Supplier Data Synchronization

```python
# Python example: Production-ready supplier sync from external system
import requests
import os
from typing import Dict, Any, Optional

class SAPBusinessPartnerClient:
    """Production-ready SAP Business Partner API client."""
    
    def __init__(self, base_url: str):
        self.base_url = base_url.rstrip('/')
        self.session = requests.Session()
        self.session.auth = (
            os.environ.get('SAP_USER'),
            os.environ.get('SAP_PASSWORD')
        )
        self.csrf_token: Optional[str] = None
    
    def _fetch_csrf_token(self) -> str:
        """Fetch CSRF token for write operations."""
        response = self.session.head(
            f"{self.base_url}/A_BusinessPartner",
            headers={'X-CSRF-Token': 'Fetch'}
        )
        response.raise_for_status()
        token = response.headers.get('X-CSRF-Token')
        if not token or token == 'Required':
            raise RuntimeError("Failed to fetch CSRF token")
        self.csrf_token = token
        return token
    
    def _post(self, endpoint: str, data: Dict[str, Any]) -> Dict[str, Any]:
        """POST with CSRF token and error handling."""
        if not self.csrf_token:
            self._fetch_csrf_token()
        
        response = self.session.post(
            f"{self.base_url}/{endpoint}",
            json=data,
            headers={
                'X-CSRF-Token': self.csrf_token,
                'Accept': 'application/json'
            }
        )
        
        if response.status_code == 403:  # CSRF expired
            self._fetch_csrf_token()
            return self._post(endpoint, data)
        
        response.raise_for_status()
        return response.json().get('d', {})

def sync_supplier(client: SAPBusinessPartnerClient, external_data: Dict[str, Any]) -> str:
    """
    Sync supplier from external system to SAP.
    
    Args:
        client: Configured SAP API client
        external_data: Dict with 'name', 'short_name', 'currency' keys
    
    Returns:
        Created Business Partner number
    
    Raises:
        requests.HTTPError: If any API call fails
    """
    try:
        # Step 1: Create Business Partner
        bp_data = {
            "BusinessPartnerCategory": "2",  # Organization
            "OrganizationBPName1": external_data['name'],
            "SearchTerm1": external_data['short_name'][:20]  # Max 20 chars
        }
        bp_result = client._post("A_BusinessPartner", bp_data)
        bp_number = bp_result['BusinessPartner']
        
        # Step 2: Assign Supplier Role
        client._post("A_BusinessPartnerRole", {
            "BusinessPartner": bp_number,
            "BusinessPartnerRole": "FLVN00"  # FI Vendor
        })
        
        # Step 3: Create Purchasing Org Data
        client._post("A_SupplierPurchasingOrg", {
            "Supplier": bp_number,
            "PurchasingOrganization": "1000",
            "Currency": external_data.get('currency', 'USD'),
            "PaymentTerms": "0001"
        })
        
        return bp_number
        
    except requests.HTTPError as e:
        # Log error details for debugging
        error_msg = e.response.text if e.response else str(e)
        raise RuntimeError(f"Failed to sync supplier: {error_msg}") from e

# Usage example
if __name__ == "__main__":
    client = SAPBusinessPartnerClient(
        os.environ.get('SAP_BASE_URL', 'https://sap-server/sap/opu/odata/sap/API_BUSINESS_PARTNER')
    )
    
    external_supplier = {
        'name': 'ACME Supplies Ltd',
        'short_name': 'ACME-SUP',
        'currency': 'EUR'
    }
    
    bp_number = sync_supplier(client, external_supplier)
    print(f"Created supplier: {bp_number}")
```


### Scenario 3: Address Validation Service

```typescript
// TypeScript example: Validate and format addresses
class AddressValidator {
  private schema: any;
  
  async validateAddress(address: BusinessPartnerAddress): Promise<ValidationResult> {
    const errors: string[] = [];
    
    // Required field validation
    if (!address.Country || address.Country.length !== 2) {
      errors.push("Country must be 2-character ISO code");
    }
    
    if (!address.CityName) {
      errors.push("City name is required");
    }
    
    if (!address.PostalCode) {
      errors.push("Postal code is required");
    }
    
    // Length validation from schema
    if (address.StreetName && address.StreetName.length > 60) {
      errors.push("Street name exceeds maximum length of 60 characters");
    }
    
    if (address.CityName && address.CityName.length > 40) {
      errors.push("City name exceeds maximum length of 40 characters");
    }
    
    // Format validation
    if (address.PostalCode && !/^[\w\s-]+$/.test(address.PostalCode)) {
      errors.push("Invalid postal code format");
    }
    
    return {
      valid: errors.length === 0,
      errors: errors
    };
  }
  
  async formatAddressForDisplay(
    businessPartner: string,
    addressId: string
  ): Promise<string> {
    // Fetch address from API
    const response = await fetch(
      `${API_URL}/A_BusinessPartnerAddress(` +
      `BusinessPartner='${businessPartner}',AddressID='${addressId}')`
    );
    const address = await response.json();
    
    // Format for display
    return `
${address.d.StreetName} ${address.d.HouseNumber}
${address.d.CityName}, ${address.d.Region} ${address.d.PostalCode}
${address.d.Country}
    `.trim();
  }
}
```

### Scenario 4: Bulk Data Import

```java
// Java example: Batch import of business partners
public class BusinessPartnerBulkImporter {
    
    private static final String BATCH_ENDPOINT = 
        "/sap/opu/odata/sap/API_BUSINESS_PARTNER/$batch";
    
    public void importBusinessPartners(List<BusinessPartnerDTO> partners) {
        StringBuilder batchRequest = new StringBuilder();
        String boundary = "batch_" + UUID.randomUUID().toString();
        
        batchRequest.append("--").append(boundary).append("\r\n");
        
        for (BusinessPartnerDTO partner : partners) {
            // Add Business Partner
            batchRequest.append("Content-Type: application/http\r\n");
            batchRequest.append("Content-Transfer-Encoding: binary\r\n\r\n");
            batchRequest.append("POST A_BusinessPartner HTTP/1.1\r\n");
            batchRequest.append("Content-Type: application/json\r\n\r\n");
            batchRequest.append(toJson(partner)).append("\r\n");
            batchRequest.append("--").append(boundary).append("\r\n");
            
            // Add Address
            batchRequest.append("Content-Type: application/http\r\n");
            batchRequest.append("Content-Transfer-Encoding: binary\r\n\r\n");
            batchRequest.append("POST A_BusinessPartnerAddress HTTP/1.1\r\n");
            batchRequest.append("Content-Type: application/json\r\n\r\n");
            batchRequest.append(toJson(partner.getAddress())).append("\r\n");
            batchRequest.append("--").append(boundary).append("\r\n");
        }
        
        batchRequest.append("--").append(boundary).append("--");
        
        // Execute batch request
        HttpClient client = HttpClient.newHttpClient();
        HttpRequest request = HttpRequest.newBuilder()
            .uri(URI.create(BASE_URL + BATCH_ENDPOINT))
            .header("Content-Type", "multipart/mixed; boundary=" + boundary)
            .POST(HttpRequest.BodyPublishers.ofString(batchRequest.toString()))
            .build();
        
        HttpResponse<String> response = client.send(request, 
            HttpResponse.BodyHandlers.ofString());
        
        processBatchResponse(response.body());
    }
}
```

### Scenario 5: Real-time Data Sync with Webhook

```javascript
// Node.js example: Webhook receiver for BP changes
const express = require('express');
const app = express();

app.post('/webhook/business-partner', async (req, res) => {
  const { event, businessPartner } = req.body;
  
  switch(event) {
    case 'CREATED':
      await handleBusinessPartnerCreated(businessPartner);
      break;
    case 'UPDATED':
      await handleBusinessPartnerUpdated(businessPartner);
      break;
    case 'DELETED':
      await handleBusinessPartnerDeleted(businessPartner);
      break;
  }
  
  res.status(200).send('OK');
});

async function handleBusinessPartnerCreated(bpNumber) {
  // Fetch full details
  const bp = await fetchBusinessPartner(bpNumber);
  const addresses = await fetchBusinessPartnerAddresses(bpNumber);
  const roles = await fetchBusinessPartnerRoles(bpNumber);
  
  // Sync to external system
  await externalSystem.syncBusinessPartner({
    businessPartner: bp,
    addresses: addresses,
    roles: roles
  });
  
  // Log sync
  console.log(`Synced new BP: ${bpNumber}`);
}

async function fetchBusinessPartner(bpNumber) {
  const response = await fetch(
    `${SAP_API_URL}/A_BusinessPartner('${bpNumber}')?` +
    `$expand=to_BusinessPartnerAddress,to_BusinessPartnerRole`
  );
  return response.json();
}
```

---

## 🎯 Use Cases & Examples

### Use Case 1: Customer 360 View

**Business Need**: Display complete customer information in one screen

**Solution**: Use schema to navigate relationships

```javascript
// Fetch customer with all related data
async function getCustomer360View(customerNumber) {
  const response = await fetch(
    `${API_URL}/A_Customer('${customerNumber}')?` +
    `$expand=` +
      `to_CustomerCompany/to_CustomerDunning,` +
      `to_CustomerSalesArea/to_PartnerFunction,` +
      `to_CustomerSalesArea/to_SalesAreaTax,` +
      `to_BusinessPartner/to_BusinessPartnerAddress/to_EmailAddress,` +
      `to_BusinessPartner/to_BusinessPartnerAddress/to_PhoneNumber,` +
      `to_BusinessPartner/to_BusinessPartnerBank`
  );
  
  const data = await response.json();
  
  return {
    basicInfo: {
      customerNumber: data.Customer,
      name: data.CustomerName,
      accountGroup: data.CustomerAccountGroup
    },
    financialInfo: data.to_CustomerCompany.results.map(cc => ({
      companyCode: cc.CompanyCode,
      paymentTerms: cc.PaymentTerms,
      creditLimit: cc.APARToleranceGroup,
      dunning: cc.to_CustomerDunning.results
    })),
    salesInfo: data.to_CustomerSalesArea.results.map(sa => ({
      salesOrg: sa.SalesOrganization,
      channel: sa.DistributionChannel,
      division: sa.Division,
      priceList: sa.PriceListType,
      shippingCondition: sa.ShippingCondition,
      partnerFunctions: sa.to_PartnerFunction.results
    })),
    contactInfo: {
      addresses: data.to_BusinessPartner.to_BusinessPartnerAddress.results,
      emails: data.to_BusinessPartner.to_BusinessPartnerAddress.results
        .flatMap(addr => addr.to_EmailAddress.results),
      phones: data.to_BusinessPartner.to_BusinessPartnerAddress.results
        .flatMap(addr => addr.to_PhoneNumber.results)
    },
    bankDetails: data.to_BusinessPartner.to_BusinessPartnerBank.results
  };
}
```

### Use Case 2: Duplicate Detection

**Business Need**: Prevent duplicate business partner creation

**Solution**: Search using schema fields

```python
def find_potential_duplicates(name, city, postal_code):
    """
    Search for existing business partners that might be duplicates
    """
    # Build search filter
    filters = [
        f"substringof('{name}', BusinessPartnerName)",
        f"substringof('{name}', BusinessPartnerFullName)",
        f"substringof('{name}', SearchTerm1)"
    ]
    
    filter_string = f"({' or '.join(filters)})"
    
    # Search business partners
    url = (
        f"{API_URL}/A_BusinessPartner?"
        f"$filter={filter_string}&"
        f"$expand=to_BusinessPartnerAddress&"
        f"$top=50"
    )
    
    response = requests.get(url)
    partners = response.json()['d']['results']
    
    # Check addresses for better matching
    potential_duplicates = []
    for partner in partners:
        for address in partner['to_BusinessPartnerAddress']['results']:
            if (address['CityName'] == city and 
                address['PostalCode'] == postal_code):
                potential_duplicates.append({
                    'businessPartner': partner['BusinessPartner'],
                    'name': partner['BusinessPartnerName'],
                    'matchScore': calculate_match_score(partner, address, 
                                                        name, city, postal_code)
                })
    
    # Sort by match score
    potential_duplicates.sort(key=lambda x: x['matchScore'], reverse=True)
    
    return potential_duplicates[:10]  # Return top 10 matches
```

### Use Case 3: Address Autocomplete

**Business Need**: Help users enter addresses quickly

**Solution**: Use address entity structure

```typescript
class AddressAutocomplete {
  async searchStreets(cityName: string, streetPrefix: string): Promise<Street[]> {
    // Search existing addresses for street suggestions
    const filter = (
      `CityName eq '${cityName}' and ` +
      `startswith(StreetName, '${streetPrefix}')`
    );
    
    const response = await fetch(
      `${API_URL}/A_BusinessPartnerAddress?` +
      `$filter=${filter}&` +
      `$select=StreetName,PostalCode&` +
      `$top=10`
    );
    
    const data = await response.json();
    
    // Deduplicate streets
    const uniqueStreets = new Map<string, Street>();
    data.d.results.forEach((addr: any) => {
      if (!uniqueStreets.has(addr.StreetName)) {
        uniqueStreets.set(addr.StreetName, {
          name: addr.StreetName,
          postalCode: addr.PostalCode
        });
      }
    });
    
    return Array.from(uniqueStreets.values());
  }
  
  async searchCities(country: string, cityPrefix: string): Promise<City[]> {
    const filter = (
      `Country eq '${country}' and ` +
      `startswith(CityName, '${cityPrefix}')`
    );
    
    const response = await fetch(
      `${API_URL}/A_BusinessPartnerAddress?` +
      `$filter=${filter}&` +
      `$select=CityName,Region,PostalCode&` +
      `$top=10`
    );
    
    const data = await response.json();
    
    // Deduplicate cities
    const uniqueCities = new Map<string, City>();
    data.d.results.forEach((addr: any) => {
      const key = `${addr.CityName}-${addr.Region}`;
      if (!uniqueCities.has(key)) {
        uniqueCities.set(key, {
          name: addr.CityName,
          region: addr.Region,
          postalCode: addr.PostalCode
        });
      }
    });
    
    return Array.from(uniqueCities.values());
  }
}
```

### Use Case 4: Credit Management Dashboard

**Business Need**: Monitor customer credit status

**Solution**: Aggregate financial data

```sql
-- SQL view based on schema (for analytics)
CREATE VIEW V_CUSTOMER_CREDIT_STATUS AS
SELECT 
  c.CUSTOMER,
  c.CUSTOMER_NAME,
  cc.COMPANY_CODE,
  cc.RECONCILIATION_ACCOUNT,
  cc.PAYMENT_TERMS,
  cc.PAYMENT_BLOCKING_REASON,
  cc.CUSTOMER_IS_BLOCKED_FOR_POSTING,
  cd.DUNNING_LEVEL,
  cd.LAST_DUNNED_ON,
  cd.DUNNING_BLOCKING_REASON,
  -- Calculate days overdue
  CASE 
    WHEN cc.PAYMENT_BLOCKING_REASON IS NOT NULL THEN 'BLOCKED'
    WHEN cd.DUNNING_LEVEL >= 3 THEN 'HIGH_RISK'
    WHEN cd.DUNNING_LEVEL = 2 THEN 'MEDIUM_RISK'
    WHEN cd.DUNNING_LEVEL = 1 THEN 'LOW_RISK'
    ELSE 'OK'
  END AS CREDIT_STATUS
FROM 
  A_CUSTOMER c
  INNER JOIN A_CUSTOMER_COMPANY cc 
    ON c.CUSTOMER = cc.CUSTOMER
  LEFT JOIN A_CUSTOMER_DUNNING cd 
    ON c.CUSTOMER = cd.CUSTOMER 
    AND cc.COMPANY_CODE = cd.COMPANY_CODE
WHERE 
  cc.CUSTOMER_IS_BLOCKED_FOR_POSTING = 'X'
  OR cd.DUNNING_LEVEL >= 1;
```

### Use Case 5: Mobile Contact App

**Business Need**: Access contact information on mobile devices

**Solution**: Lightweight API calls

```swift
// Swift example for iOS app
class ContactManager {
    let baseURL = "https://sap-server/sap/opu/odata/sap/API_BUSINESS_PARTNER"
    
    func searchContacts(query: String, completion: @escaping ([Contact]) -> Void) {
        let filter = "substringof('\(query)', BusinessPartnerFullName)"
        let url = "\(baseURL)/A_BusinessPartner?" +
                  "$filter=\(filter) and BusinessPartnerCategory eq '1'&" +
                  "$select=BusinessPartner,BusinessPartnerFullName&" +
                  "$expand=to_BusinessPartnerContact&" +
                  "$top=20"
        
        // Fetch data
        URLSession.shared.dataTask(with: URL(string: url)!) { data, _, _ in
            guard let data = data else { return }
            let partners = try? JSONDecoder().decode(BusinessPartnerResponse.self, from: data)
            
            let contacts = partners?.d.results.map { bp -> Contact in
                Contact(
                    id: bp.BusinessPartner,
                    name: bp.BusinessPartnerFullName,
                    company: bp.to_BusinessPartnerContact.results.first?.BusinessPartnerCompany,
                    department: bp.to_BusinessPartnerContact.results.first?.ContactPersonDepartment
                )
            } ?? []
            
            completion(contacts)
        }.resume()
    }
    
    func getContactDetails(businessPartner: String, completion: @escaping (ContactDetails?) -> Void) {
        let url = "\(baseURL)/A_BusinessPartner('\(businessPartner)')?" +
                  "$expand=to_BusinessPartnerAddress/to_EmailAddress," +
                  "to_BusinessPartnerAddress/to_PhoneNumber"
        
        URLSession.shared.dataTask(with: URL(string: url)!) { data, _, _ in
            guard let data = data else {
                completion(nil)
                return
            }
            
            let bp = try? JSONDecoder().decode(BusinessPartnerDetail.self, from: data)
            
            guard let partner = bp?.d else {
                completion(nil)
                return
            }
            
            let emails = partner.to_BusinessPartnerAddress.results
                .flatMap { $0.to_EmailAddress.results }
                .map { $0.EmailAddress }
            
            let phones = partner.to_BusinessPartnerAddress.results
                .flatMap { $0.to_PhoneNumber.results }
                .map { $0.InternationalPhoneNumber }
            
            let details = ContactDetails(
                businessPartner: partner.BusinessPartner,
                name: partner.BusinessPartnerFullName,
                emails: emails,
                phones: phones
            )
            
            completion(details)
        }.resume()
    }
}
```

---

## ✅ Best Practices

### For All Users

1. **Understand the Data Model**
   - Review entity relationships before starting
   - Understand required vs. optional fields
   - Know the key fields for each entity

2. **Use Standard Fields First**
   - Leverage out-of-the-box fields before creating custom ones
   - Follow SAP naming conventions
   - Respect field lengths and formats

3. **Maintain Data Quality**
   - Validate data before entry
   - Use search functionality to avoid duplicates
   - Keep addresses current and accurate

### For Functional Consultants

1. **Requirements Mapping**
   - Map business requirements to standard entities
   - Document field usage and business rules
   - Identify gaps early in the project

2. **Data Migration**
   - Create detailed mapping documents
   - Validate source data quality
   - Plan for data cleansing
   - Test with sample data first

3. **Process Design**
   - Design processes around standard entities
   - Minimize customizations
   - Document dependencies
   - Plan for scalability

4. **Testing**
   - Create comprehensive test cases
   - Test all mandatory field validations
   - Verify relationships and navigation
   - Test with realistic data volumes

### For Technical Developers

1. **API Design**
   ```javascript
   // ✅ GOOD: Select only needed fields
   GET /A_BusinessPartner('1000')?$select=BusinessPartner,BusinessPartnerName
   
   // ❌ BAD: Fetch all fields when not needed
   GET /A_BusinessPartner('1000')
   ```

2. **Performance Optimization**
   ```javascript
   // ✅ GOOD: Use $expand to fetch related data in one call
   GET /A_BusinessPartner('1000')?$expand=to_BusinessPartnerAddress
   
   // ❌ BAD: Multiple calls to fetch related data
   GET /A_BusinessPartner('1000')
   GET /A_BusinessPartnerAddress?$filter=BusinessPartner eq '1000'
   ```

3. **Error Handling**
   ```python
   # ✅ GOOD: Handle errors gracefully
   try:
       response = requests.post(url, json=data)
       response.raise_for_status()
       return response.json()
   except requests.exceptions.HTTPError as e:
       if e.response.status_code == 400:
           # Handle validation errors
           errors = e.response.json()
           log_validation_errors(errors)
       elif e.response.status_code == 409:
           # Handle duplicate key
           handle_duplicate()
       else:
           raise
   ```

4. **Batch Operations**
   ```javascript
   // ✅ GOOD: Use batch for multiple operations
   POST /$batch
   
   // ❌ BAD: Sequential API calls
   for (item of items) {
       await POST /A_BusinessPartner
   }
   ```

5. **Caching Strategy**
   ```typescript
   // ✅ GOOD: Cache stable data
   class BusinessPartnerCache {
     private cache = new Map<string, BusinessPartner>();
     private ttl = 3600000; // 1 hour
     
     async get(id: string): Promise<BusinessPartner> {
       const cached = this.cache.get(id);
       if (cached && !this.isExpired(cached)) {
         return cached.data;
       }
       
       const fresh = await this.fetch(id);
       this.cache.set(id, { data: fresh, timestamp: Date.now() });
       return fresh;
     }
   }
   ```

6. **Validation Before API Calls**
   ```python
   # ✅ GOOD: Validate before sending to API
   def create_business_partner(data):
       # Validate using schema
       errors = validate_against_schema(data, 'A_BusinessPartnerType')
       if errors:
           raise ValidationError(errors)
       
       # Only call API if validation passes
       return api.post('/A_BusinessPartner', data)
   ```

7. **Security**
   ```javascript
   // ✅ GOOD: Never expose credentials
   const config = {
     baseURL: process.env.SAP_API_URL,
     auth: {
       username: process.env.SAP_USER,
       password: process.env.SAP_PASSWORD
     }
   };
   
   // ❌ BAD: Hardcoded credentials
   const config = {
     baseURL: 'https://sap-server.com',
     auth: { username: 'admin', password: 'password123' }
   };
   ```

8. **Logging and Monitoring**
   ```python
   # ✅ GOOD: Log important operations
   def update_customer(customer_id, data):
       logger.info(f"Updating customer {customer_id}")
       start_time = time.time()
       
       try:
           result = api.patch(f'/A_Customer(\'{customer_id}\')', data)
           duration = time.time() - start_time
           logger.info(f"Customer {customer_id} updated in {duration:.2f}s")
           return result
       except Exception as e:
           logger.error(f"Failed to update customer {customer_id}: {str(e)}")
           raise
   ```

---

## 🔧 Troubleshooting

### Common Issues

#### Issue 1: "Entity not found" Error

**Problem**: Getting 404 error when querying entity

**Solutions**:
```javascript
// ✅ Check entity name is correct
GET /A_BusinessPartner('1000')  // Correct

// ❌ Wrong entity name
GET /A_Business_Partner('1000')  // Wrong - underscore instead of no space

// ✅ Check key format
GET /A_BusinessPartner('1000000')  // Correct - 10 digits with leading zeros

// ❌ Wrong key format
GET /A_BusinessPartner('1000')  // Wrong - missing leading zeros
```

#### Issue 2: Validation Errors

**Problem**: Getting 400 Bad Request with validation errors

**Solution**: Check schema for field requirements

```python
# Common validation issues and fixes:

# Issue: Field too long
data['BusinessPartnerName'] = 'Very Long Company Name That Exceeds Maximum'[:80]

# Issue: Missing required field
if 'BusinessPartnerCategory' not in data:
    data['BusinessPartnerCategory'] = '2'  # Organization

# Issue: Wrong data type
data['IsDefaultEmailAddress'] = True  # ✅ Boolean
# data['IsDefaultEmailAddress'] = 'true'  # ❌ String

# Issue: Invalid date format
data['CreationDate'] = '/Date(1609459200000)/'  # ✅ OData format
# data['CreationDate'] = '2021-01-01'  # ❌ Wrong format
```

#### Issue 3: Performance Issues

**Problem**: Slow API responses

**Solutions**:

```javascript
// ❌ BAD: Loading too much data
GET /A_Customer?$top=10000

// ✅ GOOD: Use pagination
GET /A_Customer?$top=50&$skip=0

// ❌ BAD: Expanding too many levels
GET /A_BusinessPartner?$expand=to_BusinessPartnerAddress/to_EmailAddress/...

// ✅ GOOD: Expand only what you need
GET /A_BusinessPartner?$expand=to_BusinessPartnerAddress&$select=...

// ❌ BAD: No filtering
GET /A_Customer

// ✅ GOOD: Filter on indexed fields
GET /A_Customer?$filter=CustomerAccountGroup eq 'KUNA'
```

#### Issue 4: Duplicate Key Error

**Problem**: Getting 409 Conflict when creating records

**Solution**:

```python
def create_business_partner_safe(data):
    try:
        return api.post('/A_BusinessPartner', data)
    except HTTPError as e:
        if e.response.status_code == 409:
            # Extract BP number from error
            bp_number = extract_bp_number(e.response.text)
            
            # Check if it's really a duplicate
            existing = api.get(f'/A_BusinessPartner(\'{bp_number}\')')
            
            if is_same_partner(existing, data):
                # Return existing instead of creating
                return existing
            else:
                # Generate new BP number
                data['BusinessPartner'] = generate_new_bp_number()
                return api.post('/A_BusinessPartner', data)
        else:
            raise
```

#### Issue 5: Navigation Property Not Working

**Problem**: Cannot navigate to related entities

**Solution**:

```javascript
// ❌ WRONG: Trying to access navigation property directly
GET /A_BusinessPartner('1000')/BusinessPartnerAddress

// ✅ CORRECT: Use proper navigation property name
GET /A_BusinessPartner('1000')/to_BusinessPartnerAddress

// ❌ WRONG: Multiple expands with wrong separator
$expand=to_BusinessPartnerAddress;to_BusinessPartnerRole

// ✅ CORRECT: Use comma separator
$expand=to_BusinessPartnerAddress,to_BusinessPartnerRole
```

### Debugging Tips

1. **Use Browser Developer Tools**
   - Inspect actual HTTP requests and responses
   - Check for CORS issues
   - Monitor network traffic

2. **Enable Verbose Logging**
   ```python
   import logging
   logging.basicConfig(level=logging.DEBUG)
   ```

3. **Test in Postman/Insomnia**
   - Isolate API issues from application code
   - Test different query options
   - Save successful queries for reference

4. **Check SAP Gateway Logs**
   - Transaction: /IWFND/ERROR_LOG
   - Look for detailed error messages
   - Check for authorization issues

5. **Validate JSON Structure**
   ```javascript
   // Use JSON validator
   const isValid = validateJSON(jsonString);
   
   // Check against schema
   const errors = validateAgainstSchema(data, entityType);
   ```

---

## ❓ Frequently Asked Questions

### General Questions

**Q1: What is the difference between BusinessPartner, Customer, and Supplier?**

A: 
- **BusinessPartner** is the universal master record for any business entity (person or organization)
- **Customer** is an extension of BusinessPartner with sales-specific data
- **Supplier** is an extension of BusinessPartner with purchasing-specific data
- One BusinessPartner can be both a Customer and Supplier simultaneously

```
BusinessPartner (BP Number: 1000000)
├── Customer Role (Customer Number: 1000000)
│   └── Sales Area Data
└── Supplier Role (Supplier Number: 1000000)
    └── Purchasing Org Data
```

**Q2: Can I create a Customer without creating a BusinessPartner first?**

A: No, you must first create the BusinessPartner, then extend it to Customer. The API will handle both if you use the proper navigation.

**Q3: How many email addresses can a business partner have?**

A: Unlimited. Each address can have multiple email addresses, and each is identified by the OrdinalNumber.

**Q4: What is the difference between AddressID and BusinessPartner?**

A:
- **BusinessPartner** = The person or company (e.g., "ABC Corp")
- **AddressID** = A specific location for that person/company (e.g., "Head Office", "Warehouse 1")
- One BusinessPartner can have multiple AddressIDs

**Q5: Are phone numbers stored with country codes?**

A: Yes, use these fields:
- `DestinationLocationCountry` - Country code (e.g., "US")
- `PhoneNumber` - Number with area code
- `InternationalPhoneNumber` - Complete formatted number

### Technical Questions

**Q6: What format should I use for dates?**

A: OData V2 uses this format: `/Date(1609459200000)/` (milliseconds since epoch)

```javascript
// Convert JavaScript Date to OData format
function toODataDate(date) {
  return `/Date(${date.getTime()})/`;
}

// Convert OData format to JavaScript Date
function fromODataDate(odataDate) {
  const timestamp = parseInt(odataDate.match(/\d+/)[0]);
  return new Date(timestamp);
}
```

**Q7: How do I handle special characters in filters?**

A: URL-encode special characters:

```javascript
// ✅ CORRECT
const name = "O'Brien & Associates";
const encoded = encodeURIComponent(name);
const filter = `substringof('${encoded}', BusinessPartnerName)`;

// ❌ WRONG
const filter = `substringof('O'Brien & Associates', BusinessPartnerName)`;
```

**Q8: What's the maximum number of records I can retrieve?**

A: Default is typically 1000, but this is configurable. Use pagination:

```javascript
// Paginate through large result sets
async function getAllCustomers() {
  let skip = 0;
  const top = 100;
  let allCustomers = [];
  
  while (true) {
    const response = await fetch(
      `${API_URL}/A_Customer?$top=${top}&$skip=${skip}`
    );
    const data = await response.json();
    
    if (data.d.results.length === 0) break;
    
    allCustomers = allCustomers.concat(data.d.results);
    skip += top;
  }
  
  return allCustomers;
}
```

**Q9: Can I update multiple entities in one API call?**

A: Yes, use $batch:

```javascript
POST /$batch

--batch_123
Content-Type: application/http

PATCH A_BusinessPartner('1000') HTTP/1.1
Content-Type: application/json

{"BusinessPartnerName": "Updated Name"}

--batch_123
Content-Type: application/http

POST A_BusinessPartnerAddress HTTP/1.1
Content-Type: application/json

{"BusinessPartner":"1000","Country":"US",...}

--batch_123--
```

**Q10: How do I know which fields are required?**

A: Check the schema:
- `"Nullable": false` = Required
- `"Nullable": true` or not specified = Optional
- Key fields are always required

### Business Process Questions

**Q11: What's the typical process for onboarding a new customer?**

A:
```
1. Create BusinessPartner (general data)
2. Assign Customer role
3. Create Customer general data
4. Create Customer company code data (per company code)
5. Create Customer sales area data (per sales org)
6. Add addresses (shipping, billing, etc.)
7. Add communication data (email, phone)
8. Add bank details
9. Assign partner functions (ship-to, bill-to, payer)
10. Set up payment terms and credit control
```

**Q12: Can I have different payment terms for different company codes?**

A: Yes, payment terms are maintained at the CustomerCompany level (per company code).

**Q13: How do I block a customer from creating orders?**

A: Set blocking flags in CustomerSalesArea:
- `SalesBlocked` - Block sales orders
- `DeliveryIsBlocked` - Block deliveries
- `BillingIsBlockedForCustomer` - Block billing
- `OrderIsBlockedForCustomer` - Block all order processing

**Q14: What's the difference between SalesOrganization and CompanyCode?**

A:
- **SalesOrganization** - Sales-specific organizational unit (for pricing, delivery, etc.)
- **CompanyCode** - Financial organizational unit (for accounting, payment, etc.)
- One customer can have data in multiple sales orgs and company codes

**Q15: How do I set up a customer for multiple sales areas?**

A: Create separate CustomerSalesArea records for each combination of:
- SalesOrganization
- DistributionChannel
- Division

```javascript
// Customer 1000 in Sales Org 1000, Channel 10, Division 00
POST /A_CustomerSalesArea
{
  "Customer": "1000",
  "SalesOrganization": "1000",
  "DistributionChannel": "10",
  "Division": "00",
  ...
}

// Same customer in different sales area
POST /A_CustomerSalesArea
{
  "Customer": "1000",
  "SalesOrganization": "2000",
  "DistributionChannel": "20",
  "Division": "00",
  ...
}
```

---

## 📖 Glossary

### Business Terms

| Term | Definition | Example |
|------|------------|---------|
| **Business Partner** | Any person or organization with which your company has a business relationship | Customer, Supplier, Employee, Competitor |
| **Account Group** | Classification that controls field statuses and number ranges | KUNA (Customer), KRED (Supplier/Vendor) |
| **Sales Organization** | Organizational unit responsible for sales and distribution | 1000 = US Sales, 2000 = EU Sales |
| **Distribution Channel** | Channel through which products/services reach customers | 10 = Wholesale, 20 = Retail, 30 = Online |
| **Division** | Product groups or business areas | 00 = Cross-division, 01 = Electronics |
| **Company Code** | Smallest organizational unit for external accounting | 1000 = US Company, 2000 = UK Company |
| **Purchasing Organization** | Organizational unit responsible for procurement | 1000 = Corporate Procurement |
| **Partner Function** | Role of a business partner in a transaction | SP = Sold-to Party, SH = Ship-to Party, BP = Bill-to Party, PY = Payer |
| **Dunning** | Process of reminding customers of overdue payments | Dunning Level 1, 2, 3 |
| **Reconciliation Account** | G/L account for automatic posting of customer/supplier transactions | 140000 = Domestic Customers, 200000 = Domestic Suppliers |
| **Incoterms** | International commercial terms defining delivery responsibilities | FOB = Free On Board, CIF = Cost Insurance Freight |
| **Payment Terms** | Conditions for payment (due date, discounts) | 0001 = Payable immediately, 0002 = Within 30 days |

### Technical Terms

| Term | Definition | Example |
|------|------------|---------|
| **OData** | Open Data Protocol - REST-based web service protocol | https://api.com/odata/service |
| **Entity Type** | Definition of a business object structure | A_BusinessPartnerType |
| **Entity Set** | Collection of entity instances | A_BusinessPartner (collection of all business partners) |
| **Property** | Field or attribute of an entity | BusinessPartner, BusinessPartnerName |
| **Key** | Field(s) that uniquely identify an entity instance | BusinessPartner = "1000000" |
| **Navigation Property** | Relationship to related entities | to_BusinessPartnerAddress |
| **Association** | Definition of relationship between entity types | BP (1) ←→ (*) Address |
| **Nullable** | Whether a field can contain null/empty values | Nullable: false = Required |
| **MaxLength** | Maximum character length for string fields | MaxLength: 10 |
| **Edm Type** | Entity Data Model type (OData data type) | Edm.String, Edm.Boolean, Edm.DateTime |
| **$expand** | OData query option to include related entities | ?$expand=to_BusinessPartnerAddress |
| **$filter** | OData query option to filter results | ?$filter=Country eq 'US' |
| **$select** | OData query option to choose specific fields | ?$select=BusinessPartner,BusinessPartnerName |
| **$top** | OData query option to limit result count | ?$top=50 |
| **$skip** | OData query option to skip results (pagination) | ?$skip=100 |
| **$orderby** | OData query option to sort results | ?$orderby=BusinessPartnerName asc |
| **HTTP Methods** | Standard web protocol operations | GET (read), POST (create), PATCH (update), DELETE (remove) |
| **JSON** | JavaScript Object Notation - data format | {"BusinessPartner": "1000000"} |
| **REST API** | Representational State Transfer - architectural style | Stateless, HTTP-based web service |
| **Batch Request** | Single HTTP request containing multiple operations | /$batch |
| **CSRF Token** | Security token to prevent cross-site request forgery | X-CSRF-Token header |

### SAP-Specific Terms

| Term | Definition | Example |
|------|------------|---------|
| **BP** | Business Partner | BP 1000000 |
| **FI** | Financial Accounting module | FI posting |
| **SD** | Sales & Distribution module | SD customer master |
| **MM** | Materials Management (Purchasing) module | MM supplier master |
| **G/L Account** | General Ledger account number | 140000 |
| **SAP Gateway** | Component that exposes OData services | /sap/opu/odata |
| **Transaction Code** | SAP screen identifier | BP (Business Partner), XD01 (Create Customer) |
| **Central Data** | Data stored centrally for all org units | BP general data |
| **Organizational Data** | Data specific to an organizational unit | Customer sales area data |

---

## 📚 Additional Resources

### Official Documentation

- **SAP API Business Hub**: https://api.sap.com/api/API_BUSINESS_PARTNER/overview
- **OData Protocol**: https://www.odata.org/documentation/
- **SAP Help Portal**: https://help.sap.com/

### Learning Resources

- **SAP Learning Hub**: Online courses for SAP products
- **openSAP**: Free online courses
- **SAP Community**: Forums and blogs
- **YouTube**: SAP tutorials and demos

### Tools

- **Postman**: API testing tool
- **SAP Gateway Client**: Transaction /IWFND/GW_CLIENT
- **JSON Formatter**: https://jsonformatter.org/
- **OData URI Builder**: Various online tools

### Schema Files in This Repository

1. **API_BUSINESS_PARTNER_SCHEMA.json** - Complete schema
2. **entity_type_index.json** - Quick reference
3. **CONVERSION_SUMMARY.md** - Technical details
4. **README.md** - This guide

---

## 🤝 Contributing

Found an error or want to improve this guide? Contributions are welcome!

### How to Contribute

1. Fork this repository
2. Make your changes
3. Submit a pull request
4. Describe your changes clearly

### Areas for Contribution

- Additional use cases and examples
- Language-specific code samples
- Best practices from real projects
- FAQ additions
- Error troubleshooting scenarios

---

## 📄 License

See LICENSE file for details.

---

## 📞 Support

For questions or issues:

1. **Check this README** - Most answers are here
2. **Review the schema file** - Entity definitions and properties
3. **SAP Community** - Ask questions in relevant forums
4. **Official SAP Support** - For production issues

---

## 🎓 Summary

This repository provides the complete data structure for SAP's Business Partner API. Whether you're:

- 👤 **An end user** - Understanding what data is available
- 💼 **A functional consultant** - Designing processes and migrations
- 💻 **A technical developer** - Building integrations and applications

You now have a comprehensive reference to work with Business Partner data effectively.

### Key Takeaways

✅ 36 entity types covering all business partner aspects  
✅ 622 properties with full metadata  
✅ Complete relationship mapping  
✅ Real-world examples and use cases  
✅ Best practices and troubleshooting  
✅ Multi-audience documentation  

---

<div align="center">

**Made with ❤️ for the SAP Community**

[⬆ Back to Top](#-ultimate-guide-for-sap-odata-api_business_partner)

</div>
