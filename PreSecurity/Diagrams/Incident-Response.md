# Incident Response Lifecycle

```mermaid
graph LR
    Detect[Detection] --> Analyze[Analysis]
    Analyze --> Contain[Containment]
    Contain --> Eradicate[Eradication]
    Eradicate --> Recover[Recovery]
    Recover --> Lessons[Lessons Learned]
    Lessons -.-> Detect
```

The incident response lifecycle is a structured approach to handling security incidents. The six phases are: Detection (identifying potential incidents), Analysis (assessing scope and impact), Containment (limiting damage), Eradication (removing the threat), Recovery (restoring normal operations), and Lessons Learned (improving future response).
