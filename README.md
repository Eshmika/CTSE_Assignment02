# 🌿 EcoTour AI: Intelligent Travel Planner

**EcoTour AI** is an intelligent travel planning system designed to create personalized, budget-friendly travel itineraries using modern AI technologies.

## 🚀 Overview

This project implements an AI-powered travel planner that combines multiple specialized agents to handle location research, cost estimation, and itinerary planning. The system supports both cloud-based AI services (Ollama) and local execution modes.

## ✨ Key Features

- **Multi-Agent Architecture**: Separates concerns into Planning, Research, Estimation, and Validation agents
- **Intelligent Recommendation**: Provides personalized suggestions based on destination, duration, and budget
- **Cost Optimization**: Calculates travel expenses with detailed breakdowns (accommodation, food, transport, activities)
- **Comprehensive Validation**: Ensures plans are realistic, budget-compliant, and structurally sound
- **Flexible Execution Modes**:
  - **Cloud Mode**: Uses Ollama for powerful AI-generated content
  - **Local Mode**: Runs with mock data for offline use
- **Extensive Testing**: Complete test suite with unit tests, property-based tests, and integration tests

## 🛠️ Technical Stack

- **Language**: Python 3.10+
- **Testing**: `pytest`, `pytest-cov`, `hypothesis`
- **Development**: `ruff`, `black`, `pre-commit`
- **AI**: Ollama (optional)
- **Structure**: Multi-agent system with shared tools and memory

## 📂 Project Structure

```
EcoTourAI/
├── agents/              # AI agent implementations
│   ├── planner.py       # Travel planner agent
│   ├── researcher.py    # Location research agent
│   ├── estimator.py     # Budget estimator agent
│   ├── validator.py     # Plan validator agent
│   └── base_agent.py    # Abstract base agent with memory
├── tools/               # Reusable tools and utilities
│   ├── location_data_tool.py
│   ├── cost_calculator_tool.py
│   ├── validation_tool.py
│   ├── file_saver_tool.py
│   └── helper_tools.py
├── main.py              # Main entry point and MAS orchestration
├── tests/               # Comprehensive test suite
│   └── test_*.py
├── .gitignore           # Version control ignore rules
└── README.md            # Project documentation
```

## 📋 Setup

### Prerequisites

- Python 3.10 or higher
- [Ollama](https://ollama.com/) (optional, for cloud mode)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd EcoTourAI
   ```

2. **Create virtual environment**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # Windows
   # source .venv/bin/activate  # Linux/Mac
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## 🏃 Usage

### Running the Travel Planner

```bash
# Terminal 1 - Start Ollama
ollama serve

# Terminal 2 - Run web interface
python -m streamlit run app.py
```

### Available Options

- **--destination** (required): Travel destination (e.g., "Ella", "Kandy")
- **--days** (required): Number of days for the trip
- **--budget** (optional): User's budget (LKR)
- **--accommodation** (optional): `budget`, `mid-range`, or `luxury`

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

# Run with detailed coverage report
pytest tests/ --cov=tools --cov=agents --cov-report=term
```

### Specific Test Categories

```bash
# Unit tests
pytest tests/test_tools.py -v

# Agent tests
pytest tests/test_agents.py -v

# Property-based tests
pytest tests/test_property_based.py -v

# Integration tests
pytest tests/test_integration.py -v
```

## 📋 Sample Output

### Cloud Mode Output

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

### Local Mode Output

```text
[LOCAL MODE] Travel Plan for Kandy (2 days, mid-range)
================================================

PLAN SUMMARY:

Day 1: Arrival in Kandy & Temple Visit
  - Morning: Arrive in Kandy, check into accommodation
  - Afternoon: Visit Temple of the Tooth Relic
  - Evening: Dinner at local restaurant

Day 2: Botanical Gardens & Departure
  - Morning: Explore Royal Botanical Gardens
  - Afternoon: Shopping for souvenirs
  - Evening: Depart from Kandy

COST ESTIMATE:

Accommodation: LKR 6,000 (2 nights × LKR 3,000)
Food: LKR 4,000 (2 days × LKR 2,000)
Transport: LKR 2,500 (tuk-tuk rides + local transport)
Activities: LKR 1,500 (garden entrance fee)
Total Cost: LKR 14,000

================================================
✅ PLAN VALIDATION PASSED

Budget Check:
  - Total Cost: LKR 14,000
  - Budget: LKR 15,000
  - Status: Within budget (LKR 1,000 remaining)
```

