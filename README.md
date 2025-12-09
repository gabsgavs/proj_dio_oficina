README: Service Order (OS) Control and Management System
Project Overview
This project presents the Entity-Relationship Diagram (ERD) modeling for a comprehensive Service Order (OS) control and management system tailored for an auto repair shop. The primary objective was to translate complex business requirements into a robust, normalized relational database structure. The model ensures end-to-end traceability of service costs, labor, parts, and the client approval workflow.

Key Modeling Concepts Applied
The structure was strategically designed to handle the core transactions and requirements of the repair shop, utilizing the following advanced concepts:
- Many-to-Many (NM) Relationships: Implemented via associative tables to correctly manage the composition of the OS (Services and Parts) and the inherent link between labor and required materials.
- Serviço Identificado (Identified Service): Links the OS to specific services and records Horas Trabalhadas (Hours Worked).
- Peças Necessárias (Necessary Parts): Links the OS to parts and records the Quantidade (Quantity) used.
- Recursos Essenciais (Essential Resources): Links the Tabela de Ref Mão de Obra (Labor Reference Table) to the Peças (Parts) entity, modeling the composition of the service itself.
- Normalization: Implementation of separate entities for Cliente (Client), Carros (Vehicles) (ensuring service history by license plate), and Mecânicos (Mechanics), eliminating data redundancy.
- Process Management: The Decisão (Decision) entity records the client's authorization (date and status), separating the approval event from the core OS data.
- Cost Calculation Support: The model enables dynamic calculation of the OS value by combining fixed part prices and labor costs derived from the hours worked against the established labor reference table.

Core Model Entities
- Entity Name: Ordem de Serviço (OS) | Function and Rationale: Central transaction record (PK: nOS). Links all services, parts, and personnel to the vehicle.
- Entity Name: Cliente (Client) | Function and Rationale: Stores client data (the owner).
- Entity Name: Carros (Vehicles) | Function and Rationale: Stores vehicle records (PK: Placa / License Plate). Linked 1:N to OS to track repair history.
- Entity Name: Mecânicos (Mechanics) | Function and Rationale: Stores employee data and their specialties.
- Entity Name: Decisão (Decision) | Function and Rationale: Records the client's authorization (approval/rejection) for the service proposal (1:1 with OS).
- Entity Name: Tabela de Ref Mão de Obra | Function and Rationale: Reference table for labor pricing/rates.
- Entity Name: Equipe Preenche OS | Function and Rationale: Associates the assigned mechanic team with the specific OS.

Implementation Notes
The final diagram accounts for a minor restriction in the modeling software by maintaining the AutorizacaoStatus flag in the Ordem de Serviço table. Conceptually, the authorization source-of-truth remains the Decisão entity.
