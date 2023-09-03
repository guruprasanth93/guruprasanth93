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
# Create a list of songs with their genres
songs = [
    {"title": "Song 1", "genre": "Jazz"},
    {"title": "Song 2", "genre": "Melody"},
    {"title": "Song 3", "genre": "Pop"},
    {"title": "Song 4", "genre": "Jazz"},
    {"title": "Song 5", "genre": "Pop"},
    {"title": "Song 6", "genre": "Melody"},
]

#
desired_order = ["Jazz", "Pop", "Melody"]

# Sort the songs based on the desired genre order
sorted_songs = sorted(songs, key=lambda song: desired_order.index(song["genre"]))

for song in sorted_songs:
    print(f"{song['title']}: {song['genre']}")



import pandas as pd

music_data = [
    {'track_name': 'Song 1', 'artist': 'Artist 1', 'genre': 'Rock'},
    {'track_name': 'Song 2', 'artist': 'Artist 2', 'genre': 'Pop'},
    {'track_name': 'Song 3', 'artist': 'Artist 3', 'genre': 'Jazz'},
    {'track_name': 'Song 4', 'artist': 'Artist 4', 'genre': 'Pop'},
    # Add more songs with genres
]

# Create a DataFrame from the music data
music_df = pd.DataFrame(music_data)


selected_genres = ['Rock', 'Pop']

# Filter music by selected genres
filtered_music = music_df[music_df['genre'].isin(selected_genres)]

# Display the filtered music
print("Filtered Music:")
print(filtered_music)




import pandas as pd

music_data = [
    {'track_name': 'Song 1', 'artist': 'Artist 1', 'genre': 'Rock', 'user_rating': 4.5},
    {'track_name': 'Song 2', 'artist': 'Artist 2', 'genre': 'Pop', 'user_rating': 3.7},
    {'track_name': 'Song 3', 'artist': 'Artist 3', 'genre': 'Jazz', 'user_rating': 4.9},
    {'track_name': 'Song 4', 'artist': 'Artist 4', 'genre': 'Pop', 'user_rating': 4.2},
    # Add more songs with genres and user ratings
]

# Create a DataFrame from the music data
music_df = pd.DataFrame(music_data)

# Simulated user input (selected genres and minimum user rating)
selected_genres = ['Rock', 'Pop']
min_user_rating = 4.0  # Adjust this value based on the user's preference

# Filter music by selected genres and user rating
filtered_music = music_df[(music_df['genre'].isin(selected_genres)) & (music_df['user_rating'] >= min_user_rating)]

# Display the filtered music
print("Filtered Music:")
print(filtered_music)






import pandas as pd

# Sample music dataset (replace this with your actual dataset)
music_data = [
    {'track_name': 'Song 1', 'artist': 'Artist 1', 'genre': 'Rock', 'user_rating': 4.5},
    {'track_name': 'Song 2', 'artist': 'Artist 2', 'genre': 'Pop', 'user_rating': 3.7},
    {'track_name': 'Song 3', 'artist': 'Artist 3', 'genre': 'Jazz', 'user_rating': 4.9},
    {'track_name': 'Song 4', 'artist': 'Artist 4', 'genre': 'Pop', 'user_rating': 4.2},
    {'track_name': 'Song 5', 'artist': 'Artist 5', 'genre': 'Rock', 'user_rating': 4.1},
    # Add more songs with genres and user ratings
]

# Create a DataFrame from the music data
music_df = pd.DataFrame(music_data)

# Simulated user input (selected genres and minimum user rating)
selected_genres = ['Rock', 'Pop', 'Jazz']
min_user_rating = 4.0  # Adjust this value based on the user's preference

# Filter music by selected genres and user rating
filtered_music = music_df[(music_df['genre'].isin(selected_genres)) & (music_df['user_rating'] > min_user_rating)]

# Create separate playlists for each genre
playlists = {}

for genre in selected_genres:
    genre_filtered_music = filtered_music[filtered_music['genre'] == genre]
    playlists[genre] = genre_filtered_music[['track_name', 'artist']]

# Display the playlists
for genre, tracks in playlists.items():
    print(f"{genre} Playlist:")
    print(tracks)
    print()


music_data = [
    {'track_name': 'Song 1', 'artist': 'Artist 1', 'genre': 'Rock', 'user_rating': 4.5},
    {'track_name': 'Song 2', 'artist': 'Artist 2', 'genre': 'Pop', 'user_rating': 3.7},
    {'track_name': 'Song 3', 'artist': 'Artist 3', 'genre': 'Jazz', 'user_rating': 4.9},
    {'track_name': 'Song 4', 'artist': 'Artist 4', 'genre': 'Pop', 'user_rating': 4.2},
    {'track_name': 'Song 5', 'artist': 'Artist 5', 'genre': 'Rock', 'user_rating': 4.1},
    # Add more songs with genres and user ratings
]

# Create separate playlists for each genre
rock_playlist = []
jazz_playlist = []
pop_playlist = []

# Iterate through the music data and populate the playlists based on genre
for track in music_data:
    if track['genre'] == 'Rock':
        rock_playlist.append(track)
    elif track['genre'] == 'Jazz':
        jazz_playlist.append(track)
    elif track['genre'] == 'Pop':
        pop_playlist.append(track)
# Filter the playlists based on user ratings above 4.0
rock_playlist_filtered = [track for track in rock_playlist if track['user_rating'] > 4.0]
jazz_playlist_filtered = [track for track in jazz_playlist if track['user_rating'] > 4.0]
pop_playlist_filtered = [track for track in pop_playlist if track['user_rating'] > 4.0]



# Display the filtered playlists
print("Rock Playlist (Filtered by User Rating > 4.0):")
print(rock_playlist_filtered)
print("\nJazz Playlist (Filtered by User Rating > 4.0):")
print(jazz_playlist_filtered)
print("\nPop Playlist (Filtered by User Rating > 4.0):")
print(pop_playlist_filtered)


# Sample list of songs with possible duplicates
songs = ["Song A", "Song B", "Song A", "Song C", "Song B", "Song D", "Song E", "Song D"]
unique_songs = set()
non_repeated_songs = []
for song in songs:
    # If the song is not in the set of unique songs, add it to both the set and the new list
    if song not in unique_songs:
        unique_songs.add(song)
        non_repeated_songs.append(song)

# Print the list of non-repeated songs
print("Non-repeated songs:")
for song in non_repeated_songs:
    print(song)


# Sample music preferences for two individuals
person1_music = ["song1", "song2", "song3", "song4", "song5"]
person2_music = ["song2", "song3", "song6", "song7", "song8"]

# Calculate mutual interest in music
mutual_interest = len(set(person1_music) & set(person2_music))

# Calculate the percentage of mutual interest
total_songs = len(person1_music) + len(person2_music)
percentage_mutual_interest = (mutual_interest / total_songs) * 100

print(f"Mutual interest: {mutual_interest} songs")
print(f"Percentage mutual interest: {percentage_mutual_interest:.2f}%")

