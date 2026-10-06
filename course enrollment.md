## 7. Domain Model Flowchart

```mermaid
flowchart TD
    A[Student Requests Course Enrollment]
    B[CourseEnrollment Aggregate]
    C{Student Eligible?}
    D{Course Available?}
    E{Credit Limit Exceeded?}
    F[Create Active Enrollment]
    G[Reject Enrollment]
    H[Emit CourseEnrollmentCreated Event]

    A --> B
    B --> C

    C -- No --> G
    C -- Yes --> D

    D -- No --> G
    D -- Yes --> E

    E -- Yes --> G
    E -- No --> F

    F --> H
