# Data Quality Management - Human-in-the-Loop (HLT)

A comprehensive web application for managing data quality issues through AI-powered recommendations and human oversight. This system allows users to upload Excel files, analyze data quality issues using AI, and manage remediation actions through an intuitive interface.

**Live URL**: https://team-pikachu-5f4c8.firebaseapp.com/

##  Features

- **Dashboard**: Overview of data quality metrics and pending issues
- **File Upload & Analysis**: Upload Excel files and analyze data quality issues using AI
- **Issues Management**: Browse, filter, and categorize data quality problems from uploaded files
- **AI-Powered Review**: Review AI-generated fix recommendations with confidence scores using Google Gemini
- **Human Oversight**: Approve, reject, or modify AI suggestions before implementation
- **Data Context**: Drill down into sample data and rule violations
- **History Tracking**: Monitor remediated vs. ignored issues over time
- **GCP Integration**: Generate automated GCP CLI commands for issue resolution

##  Technologies Used

### Frontend
- **React 18** - Modern React with hooks and functional components
- **TypeScript** - Type-safe development
- **Vite** - Fast build tool and development server
- **Tailwind CSS** - Utility-first CSS framework
- **shadcn/ui** - Beautiful and accessible UI components
- **React Router** - Client-side routing
- **React Query** - Server state management
- **Lucide React** - Beautiful icons

### Backend
- **Firebase, BigQuery, Cloud Run** - GCP-native services
- **Flask** - Python web framework
- **Google Gemini AI** - AI-powered analysis and recommendations
- **LangChain** - AI integration framework
- **Pandas** - Data manipulation and analysis
- **Werkzeug** - WSGI utilities

##  Prerequisites

- **Node.js** (v16 or higher) - [Install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating)
- **Python** (v3.8 or higher)
- **Google Gemini API Key** - [Get from Google AI Studio](https://makersuite.google.com/app/apikey)

##  Installation & Setup

### Frontend Setup

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd <your-project-name>
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm run dev
   ```

The frontend will be available at `http://localhost:8080`

### Backend Setup

1. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. **Install Python dependencies**
   ```bash
   pip install flask pandas langchain-google-genai werkzeug
   ```

3. **Configure API Key**
   - Open the Flask backend code
   - Replace `GEMINI_API_KEY` with your actual Google Gemini API key:
   ```python
   GEMINI_API_KEY = "your-actual-api-key-here"
   ```

4. **Start the Flask server**
   ```bash
   python app.py
   ```

The backend will be available at `http://localhost:5000`

##  Deployment

### Frontend Deployment (Vercel/Netlify)

1. **Build the project**
   ```bash
   npm run build
   ```

2. **Deploy to Firebase**
   ```bash
   firebase deploy
   ```

### Backend Deployment (Google Cloud Run/Heroku)

#### Google Cloud Run

1. **Create Dockerfile** (create in backend directory):
   ```dockerfile
   FROM python:3.9-slim
   WORKDIR /app
   COPY requirements.txt .
   RUN pip install -r requirements.txt
   COPY . .
   ENV PORT 8080
   CMD ["python", "app.py"]
   ```

2. **Create requirements.txt**:
   ```txt
   flask
   pandas
   langchain-google-genai
   werkzeug
   openpyxl
   ```

3. **Deploy to Cloud Run**:
   ```bash
   gcloud run deploy data-quality-api --source . --port 5000 --region us-central1
   ```

### Environment Variables

For production deployment, set these environment variables:

- `GEMINI_API_KEY`: Your Google Gemini API key

##  Usage

1. **Access the Application**
   - Open your browser and navigate to the deployed frontend URL
   - The dashboard will show an overview of your data quality metrics

2. **Upload Excel File**
   - Navigate to the "Issues" page
   - Click "Upload Excel File"
   - Select your Excel file and specify the sheet name
   - Click "Analyze" to process the file

3. **Review Issues**
   - After analysis, data quality issues will be displayed
   - Each issue shows the problem description and context
   - Click "Review" on any issue to see AI-generated remediation

4. **AI-Powered Remediation**
   - The Review page shows detailed analysis and suggested fixes
   - AI provides reasoning, remediation steps, and GCP CLI commands
   - Approve, reject, or modify suggestions as needed

5. **Track Progress**
   - Use the History page to monitor resolved vs. pending issues
   - Dashboard provides metrics and insights


- [ ] Data quality rule customization
- [ ] Scheduled analysis and monitoring
