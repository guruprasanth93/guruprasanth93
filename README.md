#sample filtering 

# Sample dataset (customer purchases)
purchases = [
    {"customer": "Alice", "product": "item1", "price": 10.0},
    {"customer": "Bob", "product": "item2", "price": 5.0},
    {"customer": "Alice", "product": "item3", "price": 8.0},
    {"customer": "Bob", "product": "item1", "price": 10.0},
    {"customer": "Alice", "product": "item2", "price": 5.0},
    {"customer": "Charlie", "product": "item3", "price": 8.0},
]

# Initialize a hashmap to store customer totals
customer_totals = {}

# Perform data transformation
for purchase in purchases:
    customer = purchase["customer"]
    price = purchase["price"]
    
    if customer in customer_totals:
        customer_totals[customer] += price
    else:
        customer_totals[customer] = price

# Print the transformed data
print("Customer Totals:")
for customer, total in customer_totals.items():
    print(f"{customer}: ${total:.2f}")



# segregate the data by category:displaying the total sales 
sales_data = [
    {"product": "A", "category": "Electronics", "amount": 500},
    {"product": "B", "category": "Clothing", "amount": 300},
    {"product": "C", "category": "Electronics", "amount": 700},
    {"product": "D", "category": "Books", "amount": 200},
    {"product": "E", "category": "Clothing", "amount": 150},
]

# Create an empty dictionary to store total sales by category
total_sales_by_category = {}

# Perform data transformation
for sale in sales_data:
    category = sale["category"]
    amount = sale["amount"]

    if category in total_sales_by_category:
        total_sales_by_category[category] += amount
    else:
        total_sales_by_category[category] = amount

# Display the transformed data
for category, total_sales in total_sales_by_category.items():
    print(f"Category: {category}, Total Sales: ${total_sales}")



def deduplicate_data(data, key):
    unique_data = {}  # Create a hashmap to store unique records
    deduplicated_data = []  # Create a list for deduplicated records

    for record in data:
        record_key = record[key]

        # If the record's key is not in the hashmap, add it
        if record_key not in unique_data:
            unique_data[record_key] = record
            deduplicated_data.append(record)

    return deduplicated_data

# print the data with the duplicate records
data = [
    {"id": 1, "name": "Alice"},
    {"id": 2, "name": "Bob"},
    {"id": 1, "name": "Alice"},  # Duplicate record
    {"id": 3, "name": "Charlie"},
]

deduplicated_data = deduplicate_data(data, key="id")

for record in deduplicated_data:
    print(record)


# aggregated_data based on categories
aggregated_data = {}

data = [
    {'category': 'A', 'value': 10},
    {'category': 'B', 'value': 15},
    {'category': 'A', 'value': 20},
   
]

for entry in data:
    category = entry['category']
    value = entry['value']
    if category in aggregated_data:
        aggregated_data[category] += value
    else:
        aggregated_data[category] = value

print(aggregated_data)



# display the details of the product with the product id
inventory = [
    {"product_id": "001", "product_name": "Product A", "current_stock": 50, "min_stock": 30},
    {"product_id": "002", "product_name": "Product B", "current_stock": 20, "min_stock": 40},
    {"product_id": "003", "product_name": "Product C", "current_stock": 35, "min_stock": 25},
    {"product_id": "004", "product_name": "Product D", "current_stock": 15, "min_stock": 10}
]


def display_product_details(product_id):
    for product in inventory:
        if product["product_id"] == product_id:
            print(f"Product ID: {product['product_id']}")
            print(f"Product Name: {product['product_name']}")
            print(f"Current Stock: {product['current_stock']}")
            print(f"Minimum Stock: {product['min_stock']}")
            return
    
     print(f"Product ID {product_id} not found in the inventory.")


display_product_details('002')



# categorize with the highest total sales and the sales amount 
sales_data = [
    {"product_id": "001", "category": "Electronics", "sales": 500},
    {"product_id": "002", "category": "Clothing", "sales": 700},
    {"product_id": "003", "category": "Electronics", "sales": 800},
    {"product_id": "004", "category": "Clothing", "sales": 600},
    {"product_id": "005", "category": "Electronics", "sales": 900},
    {"product_id": "006", "category": "Clothing", "sales": 750},
]

category_total_sales = {}

for sale in sales_data:
    category = sale["category"]
    sales = sale["sales"]
    
    if category in category_total_sales:
        category_total_sales[category] += sales
    else:
        category_total_sales[category] = sales

# Find the category with the highest total sales
max_category = max(category_total_sales, key=category_total_sales.get)
max_sales = category_total_sales[max_category]

# Print the category with the highest total sales and the total sales amount
print(f"Category with Highest Total Sales: {max_category}")
print(f"Total Sales Amount: {max_sales}")


# Create a dictionary to store transactions for each product ID
inventory = {}

# Function to add a transaction for a product ID
def add_transaction(product_id, transaction_type, quantity, date):
    if product_id not in inventory:
        inventory[product_id] = []
    inventory[product_id].append({"type": transaction_type, "quantity": quantity, "date": date})

# Example usage: Add transactions for Product A
add_transaction("001", "restock", 50, "2023-08-01")
add_transaction("001", "sale", 20, "2023-08-05")
add_transaction("001", "sale", 10, "2023-08-10")
add_transaction("001", "restock", 30, "2023-08-15")

# Function to calculate the current stock for a product ID
def calculate_current_stock(product_id):
    if product_id not in inventory:
        return 0
    
    current_stock = 0
    for transaction in inventory[product_id]:
        if transaction["type"] == "restock":
            current_stock += transaction["quantity"]
        elif transaction["type"] == "sale":
            current_stock -= transaction["quantity"]
    
    return current_stock

# Example usage: Calculate the current stock for Product A
current_stock_product_A = calculate_current_stock("001")
print(f"Current Stock for Product A: {current_stock_product_A}")



# Sample inventory data (list of dictionaries)
inventory = [
    {"product_id": 1, "product_name": "Product A", "quantity": 10},
    {"product_id": 2, "product_name": "Product B", "quantity": 5},
    {"product_id": 1, "product_name": "Product A", "quantity": 20},
    {"product_id": 3, "product_name": "Product C", "quantity": 15},
    {"product_id": 2, "product_name": "Product B", "quantity": 7},
]

# Create a hashmap to store product counts
product_counts = {}

for item in inventory:
    product_id = item["product_id"]
    if product_id in product_counts:
        product_counts[product_id] += 1
    else:
        product_counts[product_id] = 1

# Print the product IDs with multiple records
print("Product IDs with Multiple Records:")
for product_id, count in product_counts.items():
    if count > 1:
        print(f"Product ID {product_id}: {count} records")


#removal of the expiry items 

from datetime import date

(list ofinventory = [
    {"product_id": 1, "product_name": "Product A", "quantity": 10, "expiration_date": "2023-12-31"},
    {"product_id": 2, "product_name": "Product B", "quantity": 5, "expiration_date": "2023-10-15"},
    # Add more items here
]


    today = date.today()
    updated_inventory = [item for item in inventory if date.fromisoformat(item["expiration_date"]) >= today]
    return updated_inventory

# Call the function to remove expired items
inventory = remove_expired_items(inventory)

def remove_first_duplicate_per_product_id(inventory):
    seen_product_ids = {}  # A dictionary to keep track of last seen entries per product_id
    unique_inventory = []  # A list to store unique entries
    
    for item in inventory:
        product_id = item["product_id"]
        seen_product_ids[product_id] = item  # Update the entry for the product_id
        
    unique_inventory = list(seen_product_ids.values())
    return unique_inventory

# Sample inventory data
inventory = [
    {"product_id": 1, "product_name": "Product A", "quantity": 10},
    {"product_id": 2, "product_name": "Product B", "quantity": 5},
    {"product_id": 1, "product_name": "Product A", "quantity": 20},
    {"product_id": 3, "product_name": "Product B", "quantity": 15},
    {"product_id": 2, "product_name": "Product C", "quantity": 7},
]

unique_inventory = remove_first_duplicate_per_product_id(inventory)
for item in unique_inventory:
    print(item)


# Create an empty dictionary to store student information categorized by department
student_data = {}

# Sample student data
students = [
    {"name": "Alice", "department": "Math", "gender": "Female", "age": 22},
    {"name": "Bob", "department": "Math", "gender": "Male", "age": 23},
    {"name": "Charlie", "department": "Physics", "gender": "Male", "age": 21},
    {"name": "David", "department": "Physics", "gender": "Male", "age": 24},
    {"name": "Eve", "department": "Chemistry", "gender": "Female", "age": 22},
    {"name": "Frank", "department": "Chemistry", "gender": "Male", "age": 20},
]

# Categorize students by department, gender, and age
for student in students:
    department = student["department"]
    gender = student["gender"]
    age = student["age"]
    
    # Create department level if it doesn't exist
    if department not in student_data:
        student_data[department] = {}
    
    # Create gender level if it doesn't exist
    if gender not in student_data[department]:
        student_data[department][gender] = []
    
    # Append student to the corresponding age group
    student_data[department][gender].append({"name": student["name"], "age": age})

# Print the categorized student data
for department, department_data in student_data.items():
    print(f"Department: {department}")
    for gender, students in department_data.items():
        print(f"  Gender: {gender}")
        for student in students:
            print(f"    Name: {student['name']}, Age: {student['age']}")
class HashMap:
    def __init__(self):
        self.data = {}

    def put(self, key, value):
        self.data[key] = value

    def get(self, key):
        return self.data.get(key)

# categorize student by gender ,department and the age 
students = [
    {"name": "Alice", "department": "Math", "gender": "Female", "age": 22},
    {"name": "Bob", "department": "Math", "gender": "Male", "age": 23},
    {"name": "Charlie", "department": "Physics", "gender": "Male", "age": 21},
    {"name": "David", "department": "Physics", "gender": "Male", "age": 24},
    {"name": "Eve", "department": "Chemistry", "gender": "Female", "age": 22},
    {"name": "Frank", "department": "Chemistry", "gender": "Male", "age": 20},
]


department_map = HashMap()
gender_map = HashMap()
age_map = HashMap()

for student in students:0
    department = student["department"]
    gender = student["gender"]
    age = student["age"]

    if not department_map.get(department):
        department_map.put(department, [])
    department_map.get(department).append(student)

    if not gender_map.get(gender):
        gender_map.put(gender, [])
    gender_map.get(gender).append(student)

    if not age_map.get(age):
        age_map.put(age, [])
    age_map.get(age).append(student)

math_students = gender_map.get("Male")
for student in math_students:
    print(student)


# insert the female students into the middle 
students = [
    {"name": "Alice", "department": "Math", "gender": "Female", "age": 22},
    {"name": "Bob", "department": "Math", "gender": "Male", "age": 23},
    {"name": "Charlie", "department": "Physics", "gender": "Male", "age": 21},
    {"name": "David", "department": "Physics", "gender": "Male", "age": 24},
    {"name": "Eve", "department": "Chemistry", "gender": "Female", "age": 22},
    {"name": "Frank", "department": "Chemistry", "gender": "Male", "age": 20},
]

# Create a stack to store students
student_stack = []

# Count the number of male students
num_males = sum(1 for student in students if student["gender"] == "Male")

# Push male students onto the stack until half of them have been pushed
for student in students:
    if student["gender"] == "Male":
        if len(student_stack) < num_males // 2:
            student_stack.append(student)

# Push female students onto the stack
for student in students:
    if student["gender"] == "Female":
        student_stack.append(student)

# Push the remaining male students onto the stack
for student in students:
    if student["gender"] == "Male" and len(student_stack) < num_males:
        student_stack.append(student)

# Pop and print students from the stack
while student_stack:
    student = student_stack.pop()
    print(student)
