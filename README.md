# 🌿 EcoTour AI: Intelligent Travel Planner

**EcoTour AI** is an intelligent travel planning system designed to create personalized, budget-friendly travel itineraries using modern AI technologies.

## 🚀 Overview

This project implements an AI-powered travel planner that combines multiple specialized agents to handle location research, cost estimation, and itinerary planning. The system supports both cloud-based AI services (Ollama) and local execution modes.

## ✨ Key Features

- **Multi-Agent Architecture**: Separates concerns into Planning, Research, Estimation, and Validation agents
- **Intelligent Recommendation**: Provides personalized suggestions based on destination, duration, and budget
- **Cost Optimization**: Calculates travel expenses with detailed breakdowns (accommodation, food, transport, activities)
- **Comprehensive Validation**: Ensures plans are realistic, budget-compliant, and structurally sound
- **Extensive Testing**: Complete test suite with unit tests, property-based tests, and integration tests

## 🛠️ Technical Stack

- **Language**: Python 3.10+
- **Testing**: `pytest`, `pytest-cov`, `hypothesis`
- **AI**: Ollama (local LLM engine)
- ~8GB RAM minimum

## 📂 Project Structure

```
EcoTourAI/
├── agents/                          # 4 Agent implementations
│   ├── planner.py                   # Travel Planner Agent (Student 1)
│   ├── researcher.py                # Location Researcher Agent (Student 2)
│   ├── estimator.py                 # Budget Estimator Agent (Student 3)
│   └── validator.py                 # Plan Validator Agent (Student 4)
│
├── tools/                           # 4 Custom tools that agents use
│   ├── cost_calculator_tool.py      # Cost calculations (Student 1)
│   ├── location_data_tool.py        # Destination data (Student 2)
│   ├── validation_tool.py           # Plan validation (Student 3)
│   └── file_saver_tool.py           # File I/O operations (Student 4)
│
├── tests/                           # Comprehensive test suite
│   └── test_tools.py                # 36+ unit and integration tests
│
├── logs/                            # Execution logs
│   └── log.txt                      # Timestamped activity logs
│
├── main.py                          # CLI orchestrator
├── app.py                           # Streamlit web UI
├── ollama_client.py                 # Ollama LLM client 
├── setup_check.py                   # Setup verification 
│
├── requirements.txt                 # Python dependencies
├── README.md                        # This file
├── OLLAMA_SETUP.txt                 # Detailed Ollama setup guide 
├── COVERAGE_ANALYSIS.txt            # Requirements compliance audit 
│
├── output.txt                       # Generated travel plans
└── PROJECT_SUMMARY.md               # Project overview
```

## 📋 Setup

### Prerequisites

- Python 3.10 or higher
- [Ollama](https://ollama.com/)

### Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   ```

2. **Create virtual environment**

   ```bash
   python -m venv .venv
   source .venv/bin/activate  # Windows
   # source .venv/bin/activate  # Linux/Mac
   ```

3. **Install Ollama (https://ollama.ai)**

  ```bash
   ollama pull llama3:8b
  ```

3. **Install dependencies**

  ```bash
   pip install -r requirements.txt
  ```

4. **Verify setup**

  ```bash
   python setup_check.py
  ```

## 🏃 Usage

### Running the Travel Planner

```bash
# Terminal 1: Start Ollama server
ollama serve

# Terminal 2: Run CLI or Web UI
python main.py                    # CLI mode
# OR
python -m streamlit run app.py    # Web UI mode
```

## 🤖 System Architecture

### Multi-Agent Pipeline

```
User Input (Destination, Days, Budget)
    ↓
[Agent 1] Travel Planner
    ↓ (Itinerary)
[Agent 2] Location Researcher  
    ↓ (Enhanced Plan)
[Agent 3] Budget Estimator
    ↓ (Cost Analysis)
[Agent 4] Plan Validator
    ↓ (Validation Result)
Final Travel Plan (Saved to output.txt)
```

### Components

**AGENTS (4)** - Each agent handles a specific role:
- `TravelPlannerAgent` - Creates day-by-day itineraries using Ollama LLM
- `LocationResearchAgent` - Enhances plans with destination insights
- `BudgetEstimatorAgent` - Calculates comprehensive travel costs
- `PlanValidatorAgent` - Validates and scores final plans

**TOOLS (4)** - Custom Python functions that agents use:
- `cost_calculator_tool` - Budget calculations with breakdown
- `location_data_tool` - Static travel data for 4 destinations  
- `validation_tool` - Quality scoring algorithm
- `file_saver_tool` - Output generation and logging

**LLM INTEGRATION** - Ollama powered reasoning:
- `ollama_client.py` - HTTP REST client for llama3:8b
- Smart prompt engineering for each agent
- Fallback to mock data if Ollama unavailable
- Temperature and token configuration

**ORCHESTRATOR** - TravelPlannerMAS class:
- Sequences agents in correct order
- Passes context between agents
- Manages logging and observability
- Handles errors gracefully

---

## 🧪 Testing

The project includes a comprehensive test suite covering:

- Tool functionality
- Agent behavior
- Integration flows
- Error handling

### Run All Tests

```bash
# Run all tests with coverage
pytest tests/ --cov=tools --cov=agents

# Run with verbose output
pytest tests/ -v

```

### Test Categories Included

- Cost Calculator Tests (10)
- Location Data Tests (6)
- Validation Tests (4)
- File Operation Tests (6)
- Agent Tests (4)
- Integration Tests (1)
- Property-Based Tests (5)

**Total**: 36+ comprehensive test cases

---

## 📋 Sample Output

```text
Travel Plan for Ella (3 days, mid-range)
================================================

PLAN SUMMARY:

Day 1: Arrival in Ella & Tea Plantation Exploration
  - Morning: Arrive in Ella, check into accommodation
  - Afternoon: Ella Rock hike, scenic views
  - Evening: Dinner at local restaurant

Day 2: Waterfalls & Nine Arch Bridge
  - Morning: Visit Rawana Falls, swimming
  - Afternoon: Nine Arch Bridge photography
  - Evening: Relaxing evening in Ella

Day 3: Travel to Kandy & Departure
  - Morning: Scenic train journey to Kandy
  - Afternoon: Explore Kandy city
  - Evening: Depart from Kandy

COST ESTIMATE:

Accommodation: LKR 7,500 (3 nights × LKR 2,500)
Food: LKR 4,500 (3 days × LKR 1,500)
Transport: LKR 3,000 (train + local transport)
Activities: LKR 2,000 (park fees, entrance tickets)
Total Cost: LKR 17,000

================================================
✅ PLAN VALIDATION PASSED

Budget Check:
  - Total Cost: LKR 17,000
  - Budget: LKR 25,000
  - Status: Within budget (LKR 8,000 remaining)
```

