# Reflection: Remote Patient Monitoring Cloud Architecture

This project strengthened my understanding of how cloud services can be integrated to support remote patient monitoring workflows. I feel most confident about the overall architecture design and data flow, particularly the use of Cloud Storage as a landing zone, Cloud Functions for validation and analytics, and Cloud SQL for structured reporting. This design reflects real world healthcare data pipelines while remaining feasible for a student environment.

I am less confident about the clinical decision thresholds used for alerts and summaries. While metrics such as time-in-range and hypoglycemia exposure are well established, determining appropriate alert criteria would require clinical input and validation. I am also aware that an approved PHI environment would require more advanced security controls than those implemented here.

An alternative architecture considered was a virtual machine running the web application and scheduled scripts. This approach was not selected because it increases operational costs. The serverless approach is more scalable amd cost efficient.

With additional time and resources, I would expand this system by integrating vendor APIs directly, adopting healthcare interoperability standards such as FHIR, and adding more advanced analytics such as anomaly detection. I would also implement stronger governance features, including detailed audit logs, role based clinician access, and automated data quality monitoring.
