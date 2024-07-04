# API Gateway from scratch

## Objective

Establish a micro-services architecture based on the provided diagrams. The Users Service's signup and login endpoints should be accessible without requiring authentication. However, for all other services, authentication is a must.

All micro-services should be restricted from direct external access and should only be available via the API Gateway. Inter-micro-service communication should employ gRPC.

## Diagram

![Diagram](https://i.imgur.com/7pJxdfi.jpeg)

## Steps

1. **Introduction to Protobuf and Buf**:
    - Study and understand Protobuf specifications.
    - Get acquainted with the functionalities of the `buf` tool.
    - Learn the specifics of the `buf generate` command for code generation.

2. **Develop Protobuf Definition**:
    - Draft a clear Protobuf definition specifically for the Users Service, detailing its functionalities and endpoints.

3. **Generate Stubs from Protobuf Interfaces**:
    - Upon finalizing the Protobuf definitions, use the `buf generate` command to generate the necessary stubs for service communication.

4. **Generate SQL Components Using sqlc**:
  - Utilize the `sqlc` tool to:
    - Translate your database schema into Go types.
    - Convert your database queries into Go functions.

5. **Set Up Basic Server Framework**:
  - Combine the outputs from steps 3 and 4 to establish a rudimentary server structure. This will be based on both the gRPC code generated from Protobuf and the SQL code generated from `sqlc`.

6. **Adopt the Hexagonal Architecture**:
  - Revise the server structure to fit the hexagonal architecture model:
    - Layer 1: gRPC (entry point, auto-generated)
    - Layer 2: Business Logic (manually define interfaces for inputs and outputs)
    - Layer 3: SQL (end point, auto-generated)
  - Ensure smooth transitions between these layers by defining clear interfaces, especially between the Business Logic layer and the other two.

7. **Do the rest**
