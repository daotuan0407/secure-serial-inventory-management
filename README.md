# Secure Serial Inventory & Warehouse Management System

> Public case study version of an enterprise project.
> Organization names, internal system identifiers, operational locations, and confidential business information have been anonymized.

## Overview

This project focuses on managing serialized physical assets across multiple warehouses, branches, and operational locations.

The system supports inventory receiving, serial-range validation, two-step inventory transfers, asset dispatching, temporary serial locking, rejection handling, and asset recovery.

## My Role

**Business Analyst**
**Duration:** July 2025 – December 2025

My responsibilities included:

* Requirement elicitation and stakeholder clarification
* As-Is and To-Be process analysis
* End-to-end business process modeling
* Business rule definition
* SRS and functional requirement documentation
* UI/UX prototyping
* Serial validation logic design
* System integration analysis
* Collaboration with Developers, QA, Testers, and Technical Leads

## Business Problem

The organization managed large volumes of serialized physical assets across multiple locations.

Manual processes created several operational risks:

* Duplicate or invalid serial ranges
* Inaccurate inventory balances
* Assets being transferred or dispatched more than once
* Limited traceability across locations
* Difficulty handling rejected inventory transfers
* Inconsistent asset recovery records
* Lack of real-time inventory visibility

## Proposed Solution

```text
Asset Receiving
      ↓
Serial Range Validation
      ↓
Warehouse Inventory
      ↓
Transfer Request
      ↓
Temporary Serial Locking
      ↓
Transfer Approval / Rejection
      ↓
Asset Dispatch
      ↓
Operational Usage
      ↓
Asset Recovery
```

## Key Business Processes

The solution covers the following major processes:

1. Asset receiving and inventory ingestion
2. Serial-range creation and validation
3. Two-step inventory transfer
4. Transfer approval and rejection
5. Asset dispatching
6. Operational asset allocation
7. Asset recovery and warehouse return

## Key Features

* Serialized inventory management
* Automatic serial-range calculation
* Duplicate serial validation
* Two-step warehouse transfer
* Temporary serial locking
* Transfer approval and rejection
* Inventory integrity control
* Asset dispatch management
* Asset recovery tracking
* Integration with an external assignment system
* Audit trail and transaction history

## Key Business Rules

### Serial Range Calculation

When users enter a starting serial number and an ending serial number, the system automatically calculates the corresponding quantity.

```text
Quantity = Ending Serial - Starting Serial + 1
```

The system validates:

* Starting serial must not be greater than ending serial
* The serial range must not overlap an existing range
* The serial range must belong to the selected asset type
* All serials within the range must be available for the requested operation

### Temporary Serial Locking

When an inventory transfer request is created, all selected serials are temporarily locked.

Locked serials cannot be:

* Added to another transfer request
* Dispatched to another operational location
* Modified through inventory adjustment
* Included in another active workflow

The temporary lock is removed when:

* The transfer is completed
* The transfer is rejected
* The transfer request is cancelled

### Two-Step Inventory Transfer

The transfer workflow includes:

1. Source warehouse creates the transfer request
2. Selected serials are temporarily locked
3. Destination warehouse reviews the request
4. The destination warehouse accepts or rejects the transfer
5. Inventory ownership is updated only after successful acceptance

### Rejected Transfer Handling

If a transfer is rejected:

* Inventory remains in the source warehouse
* Temporary serial locks are released
* The rejection reason is recorded
* The request status changes to Rejected
* Users can create a new transfer request if necessary

## System Integration

The inventory module integrates with an external assignment system.

The integration allows the system to:

* Retrieve operational assignment information
* Match asset quantities with assigned capacity
* Generate secure dispatch data
* Prevent dispatching quantities greater than the assigned capacity
* Track the relationship between inventory and operational assignments

## Deliverables

* Public SRS
* End-to-End Business Process
* Activity Diagrams
* Sequence Diagrams
* Business Rules
* Functional Requirements
* UI/UX Prototype
* UAT Test Scenarios

## Tools

* Figma
* Draw.io
* Jira
* Confluence
* Microsoft Office
* SQL
* UML
* BPMN

## Confidentiality Notice

This repository is a public portfolio case study. Organization names, internal systems, locations, asset identifiers, operational data, and confidential business details have been changed or removed.
