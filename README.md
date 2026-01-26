# Payroll.py-
# Requirement 2: Function to input and return employee name
def get_employee_name():
    return input("Enter employee name (or 'End' to finish): ")

# Requirement 3: Function to input and return total hours
def get_total_hours():
    return float(input("Enter total hours worked: "))

# Requirement 4: Function to input and return hourly rate
def get_hourly_rate():
    return float(input("Enter hourly rate: "))

# Requirement 5: Function to input and return income tax rate
def get_tax_rate():
    return float(input("Enter income tax rate (as decimal, e.g., 0.2): "))

# Requirement 6: Function to calculate gross pay, income tax, and net pay
def calculate_pay(hours, rate, tax_rate):
    gross_pay = hours * rate
    income_tax = gross_pay * tax_rate
    net_pay = gross_pay - income_tax
    return gross_pay, income_tax, net_pay

# Requirement 7: Function to display individual employee data
def display_employee_data(name, hours, rate, gross, tax_rate, tax_amount, net):
    print(f"\nEmployee: {name}")
    print(f"Hours: {hours} | Rate: ${rate:,.2f}")
    print(f"Gross: ${gross:,.2f} | Tax: ${tax_amount:,.2f} | Net: ${net:,.2f}")

# Requirement 8: Function to display final totals
def display_totals(count, hours, gross, tax, net):
    print("\n" + "="*30)
    print("FINAL TOTALS")
    print(f"Total Employees: {count}")
    print(f"Total Hours:     {hours}")
    print(f"Total Gross:     ${gross:,.2f}")
    print(f"Total Tax:       ${tax:,.2f}")
    print(f"Total Net Pay:   ${net:,.2f}")
    print("="*30)

def main():
    # Variables to track totals
    total_employees = 0
    tot_hours = 0.0
    tot_gross = 0.0
    tot_tax = 0.0
    tot_net = 0.0

    # Requirement 1: Main loop terminated by typing "End"
    while True:
        name = get_employee_name()
        if name.lower() == "end":
            break
        
        # Calling input functions inside the loop
        hours = get_total_hours()
        rate = get_hourly_rate()
        tax_rate = get_tax_rate()
        
        # Calling calculation function inside the loop
        gross, tax_amt, net = calculate_pay(hours, rate, tax_rate)
        
        # Calling display function inside the loop
        display_employee_data(name, hours, rate, gross, tax_rate, tax_amt, net)
        
        # Accumulate totals for final summary
        total_employees += 1
        tot_hours += hours
        tot_gross += gross
        tot_tax += tax_amt
        tot_net += net

    # Final display outside the loop
    if total_employees > 0:
        display_totals(total_employees, tot_hours, tot_gross, tot_tax, tot_net)

if __name__ == "__main__":
    main()
