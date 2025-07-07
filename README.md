# 📞 AI Voice Appointment Reminder

An autonomous AI-based voice call system that sends voice reminders to patients about their appointments. Built using `n8n`, Google Calendar, Gemini LLM, and Retell AI, this system is designed to help hospitals and clinics reduce appointment no-shows by calling patients 12 hours before their scheduled visits.

## 🧠 How It Works

Every day at **9:00 AM**, the system:

1. **Triggers on Schedule**: The n8n workflow is triggered daily at 9 AM.
2. **Fetches Appointments**: All Google Calendar events scheduled 12 hours after (i.e., around 9 PM) are fetched.
3. **LLM Parsing**: A Gemini-based structured agent parses each event to extract details like:
   - Patient Name  
   - Phone Number  
   - Email Address  
   - Appointment Start and End Time  
4. **Voice Call Trigger**: The extracted data is passed to Retell AI API.
5. **Voice Agent**: Retell initiates a call to the patient and:
   - Reminds them about their upcoming appointment.
   - Offers options to:
     - ✅ Confirm the appointment
     - 🔁 Reschedule
     - ❓ Ask a question
     - 👨‍⚕️ Talk to a human at the clinic

## 🖼️ Workflow Diagram

![Workflow](workflow.png)

## 📋 Workflow Steps

- **Schedule Trigger (9 AM)**: Fires daily.
- **Google Calendar - Get Events**: Fetches events scheduled around 9 PM.
- **Gemini LLM Agent**: Parses appointment event details into structured output.
- **Output Parser**: Converts parsed LLM text into JSON format.
- **HTTP Request Node**: Sends data to Retell AI API to trigger voice call.

## 🔮 Future Improvements

- 📱 Add SMS/WhatsApp fallback if call is unanswered  
- 📧 Email summary to clinic of successful/failed calls  
- 🌐 Multi-language voice agent for better accessibility  
- 📊 Admin dashboard for call logs, response tracking  
- 🔁 Calendar auto-update on successful reschedule  
- 🧠 AI-driven classification of patient intent in real time  
- 🧑‍⚕️ Integration with EHR/EMR for complete history sync

