# SafeSpend is a Streamlit web application that helps users take control of their finances with the help of AI. Enter your income, expenses, savings, and debt to:

- Track monthly financial data
- Visualize spending and savings trends
- Save records by month
- Generate personalized financial advice using GPT-4

## Features

- Simple monthly input form
- Trend visualization via line charts
- Save and reset data
- Input for past months
- AI-powered advice using OpenAI's GPT-4

Component Level Design

# Detailed Object Model

# User Input and Budget Setup: This component handles all inputs provided by the user, such as income, expenses, and goal setting. It ensures data validation and triggers calculation workflows.
class UserInput:


  # Calculation Engine: This component computes budget status, savings recommendations, and alerts based on the input received.

class CalculationEngine:


  # Database: SQLite LocalDB includes Table: financial_records and Columns: date, income, expenses, goal, remaining_budget


# Interface Control: The interface between the GUI and backend is facilitated by the ViewModel, adhering to MVVM. The View sends user inputs to the ViewModel, which calls the CalculationEngine, then updates the View with results.

class ViewModel:

        
