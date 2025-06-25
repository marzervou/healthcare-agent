# healthcare-agent

Goal:Use GenAI on Databricks to automate clinical documentation — generate SOAP notes, summarize patient history, enable retrieval — for doctors to save time and gain insights.

🚀 What We Built

✅ Synthetic patient data & audio transcripts✅ SOAP note generation (ai_query)✅ Visit summaries✅ Vector Search index (with metadata)✅ Doctor RAG queries (ask questions on patient history)✅ Simulated EHR update (FHIR table)✅ Change Data Feed enabled

🗂️ Data Tables

1️⃣ mzervou.healthcare.synthetic_patient_visits

patient_id, patient_name, visit_datetime, doctor_name, department

2️⃣ mzervou.healthcare.synthetic_audio_transcripts

patient_id, patient_name, visit_datetime, doctor_name, department, audio_transcript

3️⃣ mzervou.healthcare.synthetic_audio_transcripts_enriched

patient_id, patient_name, visit_datetime, doctor_name, department, audio_transcript, soap_note, visit_summary

4️⃣ mzervou.healthcare.fhir_notes (simulated EHR table)

patient_id, visit_datetime, doctor_name, department, soap_note, note_source ('AI'), updated_at

🔍 Vector Search

Index: synthetic_audio_transcripts_index (databricks-bge-large-en)

Text indexed: visit_summary + SOAP note

Metadata: patient_id, doctor_name, visit_datetime

💻 Steps

Step 1: Generate synthetic patient visits → Table 1

Step 2: ai_query() → generate audio_transcript → Table 2

Step 3: ai_query() → generate soap_note + visit_summary → Table 3

Step 4: Index enriched notes in Vector Search (with metadata)

Step 5: Simulate EHR update: insert into fhir_notes

Step 6: RAG queries — doctor can ask:

"Summarize last visit of patient X"

"Show last SOAP note for patient X"

"Summarize last 3 visits of patient X"

