# Описание классов ИС "Делопроизводство"

## Основные классы

### Document (Документ)
- **Атрибуты:**
  - documentId: Long
  - title: String
  - type: DocumentType
  - creationDate: Date
  - author: Employee
  - status: DocumentStatus
  - content: String
  - relatedDocuments: List<Document>

- **Методы:**
  - createDocument(): Document
  - editDocument(): void
  - changeStatus(status: DocumentStatus): void
  - archiveDocument(): void
  - getDocumentHistory(): List<DocumentHistory>

### Employee (Сотрудник)
- **Атрибуты:**
  - employeeId: Long
  - fullName: String
  - login: String
  - passwordHash: String
  - position: String
  - department: Department
  - contactInfo: ContactInfo
  - status: EmployeeStatus

- **Методы:**
  - createEmployee(): Employee
  - editEmployee(): void
  - assignDepartment(department: Department): void
  - getDocuments(): List<Document>
  - getTasks(): List<Task>

### Department (Подразделение)
- **Атрибуты:**
  - departmentId: Long
  - name: String
  - function: String
  - head: Employee
  - employees: List<Employee>

- **Методы:**
  - createDepartment(): Department
  - editDepartment(): void
  - assignHead(employee: Employee): void
  - addEmployee(employee: Employee): void
  - removeEmployee(employee: Employee): void

### Task (Задача)
- **Атрибуты:**
  - taskId: Long
  - title: String
  - status: TaskStatus
  - assignee: Employee
  - associatedDocument: Document
  - deadline: Date
  - description: String

- **Методы:**
  - createTask(): Task
  - assignEmployee(employee: Employee): void
  - changeStatus(status: TaskStatus): void
  - editTask(): void

### ApprovalRoute (Маршрут согласования)
- **Атрибуты:**
  - routeId: Long
  - document: Document
  - routeName: String
  - steps: List<ApprovalStep>
  - status: ApprovalStatus

- **Методы:**
  - createRoute(): ApprovalRoute
  - addStep(step: ApprovalStep): void
  - startApproval(): void
  - completeApproval(): void
  - cancelApproval(): void
