# 🏨 Hotel Voice Agent - AI Hotel Concierge System

A sophisticated AI-powered hotel concierge system featuring real-time voice interactions, intelligent conversation parsing, and comprehensive guest management. Built with AWS Bedrock, Streamlit, and DynamoDB.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![AWS](https://img.shields.io/badge/AWS-Bedrock-orange.svg)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-red.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## ✨ Features

### 🎤 Real-Time Voice Processing
- Bidirectional audio streaming with AWS Bedrock
- High-quality voice synthesis and recognition
- Real-time conversation processing with PyAudio
- Configurable audio settings (16kHz input, 24kHz output)

### 🤖 Intelligent AI Agent
- Advanced conversational AI using Amazon Titan models
- Context-aware responses for hotel services
- Tool usage tracking and analytics
- Multi-turn conversation management

### 📊 Live Monitoring Dashboard
- Real-time conversation visualization with Streamlit
- Interactive log parsing and event filtering
- Usage analytics and performance metrics
- Auto-refresh capabilities for live updates

### 🗄️ Guest Management System
- DynamoDB-powered guest database
- Reservation management and tracking
- Guest profile and preference storage
- Scalable NoSQL data architecture

### 🔍 Advanced Log Analysis
- Sophisticated log parsing engine
- Event categorization (user, assistant, tool usage)
- Timestamp-based conversation reconstruction
- Pattern recognition for tool interactions

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Voice Input   │───▶│  AWS Bedrock    │───▶│  AI Processing  │
│   (PyAudio)     │    │  Runtime        │    │  & Responses    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  Conversation   │    │   Log Files     │    │   DynamoDB      │
│   Parsing       │    │   Analysis      │    │   Storage       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 ▼
                    ┌─────────────────┐
                    │  Streamlit      │
                    │  Dashboard      │
                    │  Visualization  │
                    └─────────────────┘
```

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- AWS Account with Bedrock access
- DynamoDB permissions
- Audio input/output device

### AWS Configuration
Before running the application, you need to configure your AWS credentials. You can do this in one of the following ways:

**Option 1: .env File (Recommended)**
Create a `.env` file in the project root:
```env
AWS_ACCESS_KEY_ID=your-access-key-id
AWS_SECRET_ACCESS_KEY=your-secret-access-key
AWS_DEFAULT_REGION=us-east-1
```
The application will automatically load these variables from the `.env` file using `python-dotenv`.

**Option 2: Environment Variables**
```bash
export AWS_ACCESS_KEY_ID="your-access-key-id"
export AWS_SECRET_ACCESS_KEY="your-secret-access-key"
export AWS_DEFAULT_REGION="us-east-1"
```

**Option 3: AWS CLI Configuration**
```bash
aws configure
# Follow the prompts to enter your AWS credentials
```

**Required AWS Services:**
- **Amazon Bedrock** with access to `amazon.nova-sonic-v1:0` model
- **DynamoDB** with read/write permissions for the hotel database tables

**Note:** If using a `.env` file, install `python-dotenv` and the application will automatically load the variables.

### Installation

1. **Clone the repository**
   ```bash
   git clone git@github.com:joker7blue/hotel-voice-agent.git
   cd hotel-voice-agent
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure AWS credentials**
   
   Create a `.env` file in the project root with your AWS credentials:
   ```bash
   cp .env.example .env  # If you have an example file
   # Or create .env manually with:
   echo "AWS_ACCESS_KEY_ID=your-access-key-id" > .env
   echo "AWS_SECRET_ACCESS_KEY=your-secret-access-key" >> .env
   echo "AWS_DEFAULT_REGION=us-east-1" >> .env
   ```
   
   Alternatively, use environment variables or AWS CLI as described in the AWS Configuration section.

5. **Set up the database**
   ```bash
   python db_setup.py
   ```

### Usage

1. **Start the monitoring dashboard**
   ```bash
   streamlit run app.py
   ```

2. **Run the hotel agent**
   ```bash
   python hotel_agent.py
   ```

3. **Access the dashboard**
   Open your browser to `http://localhost:8501`

## 📁 Project Structure

```
hotel-voice-agent/
├── app.py                 # Streamlit monitoring dashboard
├── hotel_agent.py         # Main AI concierge agent
├── db_setup.py           # Database initialization
├── requirements.txt      # Python dependencies
├── .env.example          # Environment variables template
├── assistant.log         # Conversation logs (generated)
└── README.md            # This file
```

## 🔧 Configuration

### Audio Settings
```python
INPUT_SAMPLE_RATE = 16000   # Voice input quality
OUTPUT_SAMPLE_RATE = 24000  # Voice output quality
CHANNELS = 1               # Mono audio
CHUNK_SIZE = 1024          # Audio buffer size
```

### AWS Configuration
- **Region**: us-east-1 (configurable via `AWS_DEFAULT_REGION`)
- **Services**: Bedrock Runtime, DynamoDB
- **Models**: Amazon Titan (voice-enabled)
- **Credentials**: Set via environment variables or AWS CLI

### Monitoring Settings
```python
MAX_EVENTS = 300           # Dashboard display limit
DEFAULT_LOG_PATH = "assistant.log"
```

## 🎯 Key Components

### Hotel Agent (`hotel_agent.py`)
- Real-time voice conversation handling
- AWS Bedrock integration for AI responses
- Audio streaming and processing
- Guest interaction management

### Dashboard (`app.py`)
- Live conversation visualization
- Log parsing and event extraction
- Interactive filtering and search
- Performance metrics display

### Database Setup (`db_setup.py`)
- DynamoDB table creation
- Demo data population
- Guest and reservation schema management

## 🛠️ Technologies Used

- **Python 3.8+**: Core programming language
- **AWS Bedrock**: AI model runtime and voice synthesis
- **Streamlit**: Interactive web dashboard
- **DynamoDB**: NoSQL database for guest data
- **PyAudio**: Real-time audio processing
- **Boto3**: AWS SDK for Python
- **RxPY**: Reactive programming for audio streams

## 📈 Performance Features

- **Real-time Processing**: Sub-second response times
- **Scalable Architecture**: Cloud-native AWS services
- **Memory Efficient**: Streaming audio processing
- **Concurrent Handling**: Multiple guest interactions
- **Monitoring**: Comprehensive logging and analytics

## 🔒 Security & Privacy

- AWS IAM-based access control
- Encrypted data transmission
- Secure credential management
- Guest data privacy compliance
- Audit logging for all interactions

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Powered by AWS Bedrock and Amazon Titan
- Inspired by modern hotel concierge systems

## 📞 Support

For questions or issues, please open a GitHub issue or contact the maintainers.

---

**⭐ Star this repo if you find it useful!**

*Showcasing advanced AI integration, real-time systems, and cloud architecture.*