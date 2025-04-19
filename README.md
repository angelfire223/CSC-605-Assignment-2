# CSC-605-Assignment-2
Component Level Design

# User Input and Budget Setup: This component handles all inputs provided by the user, such as income, expenses, and goal setting. It ensures data validation and triggers calculation workflows.

# Detailed Object Model
class UserInput:
    def __init__(self, income, expenses, goal):
        self.income = income
        self.expenses = expenses
        self.goal = goal

    def get_income(self):
        return self.income

    def get_expenses(self):
        return self.expenses

    def get_goal(self):
        return self.goal

    def set_income(self, income):
        self.income = income

    def set_expenses(self, expenses):
        self.expenses = expenses

    def set_goal(self, goal):
        self.goal = goal

  # Calculation Engine: This component computes budget status, savings recommendations, and alerts based on the input received.

class CalculationEngine:
    def calculate_remaining_budget(self, user_input):
        return user_input.get_income() - user_input.get_expenses()

    def is_goal_achievable(self, user_input):
        return self.calculate_remaining_budget(user_input) >= user_input.get_goal()

    def get_alert(self, user_input):
        remaining = self.calculate_remaining_budget(user_input)
        if remaining < 0:
            return "Over budget!"
        elif remaining < user_input.get_goal():
            return "Near limit"
        else:
            return "On track"

  # Database: SQLite LocalDB includes Table: financial_records and Columns: date, income, expenses, goal, remaining_budget

  CREATE TABLE financial_records (
    date TEXT PRIMARY KEY,
    income REAL,
    expenses REAL,
    goal REAL,
    remaining_budget REAL
);

# Interface Control: The interface between the GUI and backend is facilitated by the ViewModel, adhering to MVVM. The View sends user inputs to the ViewModel, which calls the CalculationEngine, then updates the View with results.

class ViewModel:
    def __init__(self):
        self.user_input = None
        self.engine = CalculationEngine()

    def update_user_input(self, income, expenses, goal):
        self.user_input = UserInput(income, expenses, goal)

    def get_status(self):
        return self.engine.get_alert(self.user_input)

    def get_remaining_budget(self):
        return self.engine.calculate_remaining_budget(self.user_input)
        
