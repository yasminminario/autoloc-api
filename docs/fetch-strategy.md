
# AutoLoc Fetch Strategy

## Association Strategies

| Association | Fetch | Cascade | Justification |
|---|---|---|---|
| Contract -> Payment | LAZY | ALL + orphanRemoval | Payments depend on their contract and are deleted with it. |
| Agency -> Vehicle | LAZY | None | Vehicles must survive the deletion of an agency. |
| Agency -> Employee | LAZY | None | Employees have an independent lifecycle. |
| Vehicle <-> Equipment | LAZY | None | Equipment can be shared between multiple vehicles. |
| Customer -> Reservation | LAZY | PERSIST | New reservations can be persisted with their customer. |
| Reservation -> Vehicle | LAZY | None | Vehicles exist independently of reservations. |
| Reservation <-> Contract | LAZY | ALL on Reservation side | The contract lifecycle is managed through the reservation. |
| Vehicle -> Maintenance | LAZY | PERSIST | New maintenance records can be persisted with their vehicle. |

## Fetch Strategies

### LAZY

LAZY loading retrieves associated data only when needed
within an active persistence context.

Advantages:
- Reduces unnecessary queries.
- Avoids loading large collections automatically.
- Improves efficiency for common operations.

### EAGER

EAGER loading retrieves associated data as part of
loading the owning entity.

Disadvantages:
- May load unnecessary data.
- Can increase database workload
- May negatively affect performance.

## Cascade Strategies

### CascadeType.ALL

Propagates persistence operations like
merge and remove.

Used for:
- Contract -> Payment
- Reservation -> Contract

### CascadeType.PERSIST

Propagates persistence of new associated entities.

Used for:
- Customer -> Reservation
- Vehicle -> Maintenance

### No Cascade

Used when associated entities have independent lifecycles.

Examples:
- Agency -> Vehicle
- Vehicle <-> Equipment
- Reservation -> Vehicle

## Orphan Removal

orphanRemoval = true is configured for Contract -> Payment.

Removing a payment from the contract's collection
will cause the payment to be deleted from the database
when the change is synchronized by JPA
