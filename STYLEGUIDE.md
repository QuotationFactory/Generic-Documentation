# Quotation Factory Software Development Style Guide

Welcome to the Quotation Factory software development style guide. This guide outlines our coding standards and architectural approaches to ensure our codebase remains clean, maintainable, and efficient. Below, you will find the key libraries and patterns we use in our .NET applications, including the rationale for their use and guidelines on how to implement them effectively.

## Contents

1. [Units of Measure: Using UnitsNet](#units-of-measure-using-unitsnet)
2. [Currency: Using NodaMoney](#currency-using-nodamoney)
3. [Architecture: Applying CQRS with MediatR](#architecture-applying-cqrs-with-mediatr)

## Units of Measure: Using UnitsNet

### What is UnitsNet?

UnitsNet is a library that provides a way to express and convert between different units of measurement in .NET applications. It helps in making units of measure explicit in our code, reducing errors related to unit conversions and improving the clarity of numerical calculations.

### Why Use UnitsNet?

- **Clarity and Safety:** Using explicit units of measure can prevent errors from incorrect assumptions about what units are being used.
- **Maintainability:** Code that clearly specifies units of measure is easier to understand and maintain.
- **Flexibility:** Easily convert between units when necessary without manual calculations.

### Guidelines for Using UnitsNet:

- Always use UnitsNet types when variables, parameters, or return types involve units of measurement.
- When performing operations involving units, ensure that units are compatible.
- Document any non-obvious unit transformations or reasons for specific unit choices.

## Currency: Using NodaMoney

### What is NodaMoney?

NodaMoney is a .NET library that provides robust handling of monetary values and currencies. It supports operations involving money, such as arithmetic operations and currency conversion, ensuring that these operations are accurately and clearly expressed in the code.

### Why Use NodaMoney?

- **Accuracy:** Handles monetary calculations accurately to prevent rounding errors and other common financial computation issues.
- **Clarity:** Makes the currency explicit in monetary amounts, which is crucial for international applications.
- **Standardization:** Provides a standard way to deal with different currencies, which can be particularly useful in a globalized environment like ours.

### Guidelines for Using NodaMoney:

- Use `Money` type for representing amounts of money throughout the application.
- Always specify the currency explicitly when creating `Money` objects.
- Use provided methods for currency operations and conversions to maintain accuracy.

## Architecture: Applying CQRS with MediatR

### What is CQRS?

Command Query Responsibility Segregation (CQRS) is an architectural pattern that separates reading data (query) from modifying data (command). This separation allows for more flexible and optimized handling of operations, particularly in complex application domains.

### What is MediatR?

MediatR is a .NET library that implements the mediator pattern, facilitating the implementation of CQRS by decoupling in-process messaging. Commands and queries are handled by different handlers that can operate independently, improving scalability and maintainability.

### Why Use CQRS with MediatR?

- **Scalability:** Separating reads from writes allows each to be scaled independently.
- **Maintainability:** Simplifies the business logic by separating the command and query responsibilities.
- **Performance:** Enables performance optimizations such as read/write splitting and event sourcing.

### Guidelines for Using CQRS with MediatR:

- Define separate models for reads and writes. Use read models to optimize query operations and write models for update operations.
- Use MediatR handlers for commands and queries. Ensure each command or query handler has a single responsibility.
- Avoid business logic in controllers or API endpoints; instead, delegate work to the appropriate MediatR handlers.

By adhering to this style guide and using these libraries and patterns, we aim to create a robust, scalable, and maintainable codebase. Always ensure that the principles of clarity and purpose guide your implementation choices.
