# Python-Project-007-train-data

import requests
import json

# Define the API endpoint and your API key (if required)
api_endpoint = "https://api.example.com/train-schedules"
api_key = "YOUR_API_KEY"

# Define the parameters for the API request
params = {
    'origin': 'NYC',
    'destination': 'Boston',
    'date': '2024-06-04',
    'apikey': api_key
}

# Make the API request
response = requests.get(api_endpoint, params=params)

# Check if the request was successful
if response.status_code == 200:
    # Parse the JSON response
    train_data = response.json()
    
    # Print the train data
    print(json.dumps(train_data, indent=4))
else:
    print(f"Failed to retrieve data: {response.status_code}")

# Optionally, save the data to a file
with open('train_data.json', 'w') as f:
    json.dump(train_data, f, indent=4)
