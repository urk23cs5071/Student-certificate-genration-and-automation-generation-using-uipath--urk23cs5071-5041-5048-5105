<!-- PROJECT-CONTEXT:START -->
<!-- discovery-metadata: cs=0 xaml=2 deps=5 -->
# Project Context

- Project: `Send-Certificate-in-mail` process (`project.json`), Windows framework (`targetFramework: Windows`), .NET `net10.0`.
- Expression language: Visual Basic (`expressionLanguage: VisualBasic`).
- Dependencies: `UiPath.Excel.Activities 3.6.1`, `UiPath.Mail.Activities 2.12.10`, `UiPath.System.Activities 26.10.0`, `UiPath.Testing.Activities 25.10.3`, `UiPath.UIAutomation.Activities 26.10.6`.
- Entry point: `Main.xaml` only (process entry point; no inputs or outputs).
- Workflow structure: `Main.xaml` is the orchestrator. It logs safe/test mode, conditionally retrieves the Orchestrator credential `CertificateEmailCredential` when `sendEmails` is enabled, invokes `ProcessStudents.xaml`, and displays totals for students, certificates, sent emails, failed records, and skipped emails. `sendEmails` defaults to `False`.
- `ProcessStudents.xaml` is a child workflow with 8 inputs (project path, email mode/credential, SMTP settings, organization name) and 5 outputs (student, certificate, sent-email, failure, and skipped-email counts). Its `InvokeCode` reads `Data/Students.xlsx`, validates `StudentName`, `RegisterNumber`, `Course`, and `Email`, creates non-overwriting PDFs under `Certificates`, appends `Logs/certificate-processing.csv`, skips email in safe mode or for `@example.com`, and optionally sends SMTP mail with the PDF attached.
- Preserve the existing Windows framework and Visual Basic expression language; `Main.xaml` is the sole process entry point and `ProcessStudents.xaml` is invoked as a child workflow.
<!-- PROJECT-CONTEXT:END -->
