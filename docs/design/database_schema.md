# Схема базы данных ИС "Делопроизводство"

## Основные таблицы

### documents
- id (PK)
- title
- doc_type_id (FK)
- creation_date
- author_id (FK)
- status_id (FK)
- content
- last_modified_date
- last_modified_by_id (FK)
- version

### employees
- id (PK)
- full_name
- login
- password_hash
- position
- department_id (FK)
- email
- phone
- status_id (FK)
- created_at
- last_login_at

### departments
- id (PK)
- name
- function
- head_id (FK)
- created_at
- modified_at

### document_types
- id (PK)
- name
- description
- retention_period
- is_active

### document_statuses
- id (PK)
- name
- description
- is_active

### contractors
- id (PK)
- name
- contractor_type_id (FK)
- contact_person
- email
- phone
- address
- created_at
- modified_at

### tasks
- id (PK)
- title
- description
- status_id (FK)
- assignee_id (FK)
- document_id (FK)
- deadline
- created_at
- created_by_id (FK)
- completed_at

### approval_routes
- id (PK)
- name
- document_id (FK)
- status_id (FK)
- created_at
- created_by_id (FK)
- completed_at

### approval_steps
- id (PK)
- route_id (FK)
- approver_id (FK)
- status_id (FK)
- order_num
- comment
- action_date

### document_folders
- id (PK)
- name
- parent_id (FK)
- owner_id (FK)
- created_at

### document_folder_items
- folder_id (PK, FK)
- document_id (PK, FK)
- added_at
- added_by_id (FK)

### access_rights
- id (PK)
- object_type
- object_id
- employee_id (FK)
- access_level
- granted_at
- granted_by_id (FK)
- expiry_date

### document_templates
- id (PK)
- name
- doc_type_id (FK)
- content
- created_at
- created_by_id (FK)
- is_active
- version

## Связи между таблицами

1. documents.doc_type_id -> document_types.id
2. documents.author_id -> employees.id
3. documents.status_id -> document_statuses.id
4. employees.department_id -> departments.id
5. departments.head_id -> employees.id
6. tasks.assignee_id -> employees.id
7. tasks.document_id -> documents.id
8. approval_routes.document_id -> documents.id
9. approval_steps.route_id -> approval_routes.id
10. approval_steps.approver_id -> employees.id
11. document_folders.parent_id -> document_folders.id
12. document_folders.owner_id -> employees.id
13. document_folder_items.folder_id -> document_folders.id
14. document_folder_items.document_id -> documents.id
15. access_rights.employee_id -> employees.id
16. document_templates.doc_type_id -> document_types.id
