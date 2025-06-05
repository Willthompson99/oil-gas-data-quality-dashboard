
# Alation-Style Data Documentation

## Business Terms
| Term             | Definition                                      |
|------------------|-------------------------------------------------|
| Well_ID          | Unique identifier for each well                 |
| Volume_Produced  | Total oil or gas produced by a well (in bbls)   |
| Spud_Date        | Date when drilling began on the well            |
| Prod_Start       | Start date of production for the well           |
| Prod_End         | End date of production for the well             |
| Operator         | Company operating the well                      |
| Status           | Current state of the well (e.g., Active)        |

## Data Entry Guidelines
- `Volume_Produced` must be numeric and non-negative
- `Prod_End` must be on or after `Prod_Start`
- `Well_ID` must be unique
- `Operator` must not be null

## Data Flow Diagram
ProCount (source) → SQLite → Power BI → Stakeholder Dashboard

## Notes
This documentation simulates the type of metadata captured in Alation for business and technical stakeholders.
