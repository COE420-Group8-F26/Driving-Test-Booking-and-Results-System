# Architectural Style Selection

**System:** Driving Test Booking and Results System

## Selected Architectural Style

**3-Layer Architectural Style (closed layered architecture).**

The system is decomposed into three hierarchically ordered subsystems: a user interface, a middleware (application) layer and a database layer. The 3-Layer style is a special case of the Layered style, and in a closed architecture each layer can only call the layer directly below it.

## Main Characteristics

- **Hierarchy:** a layer only depends on services from lower layers and has no knowledge of higher layers. Hierarchy reduces complexity.
- **Closed architecture:** the presentation layer never talks to the data layer directly. It always goes through the application layer.
- **Partitions:** a layer can be divided into independent subsystems that provide services to other partitions on the same layer.
- **Very low coupling and high coherence:** a change inside one layer does not affect the others as long as its interface stays the same, and each partition groups classes that work on the same task.

## Why It Is Appropriate for the Project

- **It matches our models.** Our Lab 5 class diagram already separates manager classes (business logic) from entity classes (data), and our Lab 6 sequence diagrams show the user interface calling a manager, which then calls the entities. Those classes group naturally into the three layers.
- **The business rules need one place.** Rules such as the 30-minute booking cutoff, the double-booking check and the examiner conflict check must behave the same way for every use case. In this style they all live in the application layer.
- **It is a web system with three roles.** Each role uses the same web interface, and none of them should reach the database directly (NFR-11).
- **Independent parts help the team.** Subsystems that are independent can be implemented by different team members in parallel, which fits how we divided the use cases.

## How It Supports the Design Goals

| Goal | How the style supports it |
|:--|:--|
| **DG-01 Security** | Because the architecture is closed, every request passes through the application layer, where `Session` and the role checks run before the data layer is reached. The database is never exposed to the interface. |
| **DG-02 Reliability and Data Integrity** | Booking rules and transactions are applied in the application layer, and consistency rules (links between bookings, slots, applicants and results) are enforced in the data layer. |

## Advantages and Limitations

**Advantages**

- Hierarchy reduces complexity and makes the system easy to explain and divide among team members.
- Closed architectures are more portable and give very low coupling.
- The user interface and the database can be changed independently of each other.
- Business rules and data integrity are handled in one clear place.

**Limitations**

- Closed architectures are less efficient than open ones, because every request passes through each layer in turn.