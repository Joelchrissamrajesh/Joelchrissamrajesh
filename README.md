import time
import random
import requests

# Simulate a water consumption sensor reading
def read_water_sensor():
    # Replace this with code to read data from your actual sensor
    return random.randint(1, 100)  # Replace with real sensor data

# Send data to a cloud-based platform
def send_data_to_cloud(data):
    # Replace with the URL and authentication details of your cloud platform
    api_url = "https://your-cloud-api-url.com"
    headers = {
        "Authorization": "Bearer your-api-key",
        "Content-Type": "application/json",
    }
    payload = {"water_consumption": data}  # Adjust the data structure as needed

    try:
        response = requests.post(api_url, json=payload, headers=headers)
        if response.status_code == 200:
            print("Data sent successfully.")
        else:
            print(f"Failed to send data. Status code: {response.status_code}")
    except Exception as e:
        print(f"Error: {str(e)}")

# Main program loop
while True:
    water_data = read_water_sensor()
    send_data_to_cloud(water_data)
    
    # Adjust the time interval as needed (e.g., once per hour)
    time.sleep(3600)
