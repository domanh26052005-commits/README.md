### 1.3 System Screens Flow

This diagram illustrates the navigation paths, system screens, and the relationships among screens for the VIVAS Internal Training Management System. 

*Note: Rectangular nodes represent standard flat screens, while oval nodes represent pop-up windows or modals (e.g., Test Score Pop-up, Assign Course Modal) as per the design guidelines.*

```mermaid
flowchart LR
    %% System Entry
    Login[Login via AIO] --> Dashboard[Main Dashboard]
    
    %% Common Screens
    Dashboard --> UserProfile[User Profile]
    
    %% -------------------------------------
    %% 1. EMPLOYEE LEARNING FLOW
    %% -------------------------------------
    Dashboard --> CourseList[My Courses / Public]
    CourseList --> CourseDetails[Course Details]
    CourseDetails --> StudyLecture[Lecture View Video/Text]
    StudyLecture --> TakeTest[Take Final Test]
    
    %% Pop-up for test results
    TakeTest --> TestResult([Test Score Pop-up])
    TestResult --> CourseHistory[Learning History]
    CourseDetails --> CourseHistory

    %% -------------------------------------
    %% 2. INTERNAL NEWS FLOW
    %% -------------------------------------
    Dashboard --> NewsFeed[News Feed]
    NewsFeed --> NewsDetail[News Article & Comments]
    Dashboard --> ManageNews[Manage News]
    ManageNews --> EditNews[Create/Edit News]

    %% -------------------------------------
    %% 3. COURSE & TEST MANAGEMENT (TRAINING STAFF)
    %% -------------------------------------
    Dashboard --> CourseMgmt[Course Management]
    CourseMgmt --> EditCourse[Create/Update Course]
    CourseMgmt --> AssignModal([Assign to Employees])
    
    Dashboard --> TestMgmt[Test Management]
    TestMgmt --> EditTest[Create/Update Test]
    EditTest --> ManageQuestions[Manage Questions]

    %% -------------------------------------
    %% 4. APPROVAL FLOW (HEAD OF TRAINING)
    %% -------------------------------------
    Dashboard --> Approvals[Approval Queue]
    Approvals --> ReviewDetails[Review Course/Test Details]

    %% -------------------------------------
    %% 5. REPORTS & ANALYTICS (MANAGERS & HEAD)
    %% -------------------------------------
    Dashboard --> ReportDashboard[Reports & Statistics]
    ReportDashboard --> DeptStats[Department Progress]
    ReportDashboard --> EmpStats[Employee Detail Record]

    %% -------------------------------------
    %% 6. SYSTEM ADMINISTRATION (ADMIN)
    %% -------------------------------------
    Dashboard --> UserMgmt[User Management]
    Dashboard --> SysSettings[System Settings]
    SysSettings --> EditCategory([Category Update Pop-up])

    %% Styling configurations
    classDef default fill:#f8f9fa,stroke:#343a40,stroke-width:1px;
    classDef popup fill:#e9ecef,stroke:#0056b3,stroke-width:2px,stroke-dasharray: 5 5;
    
    class TestResult,AssignModal,EditCategory popup;
