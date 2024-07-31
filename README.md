# Spring Boot and Python Integration

## Introduction

This project demonstrates how to create RESTful services using Spring Boot and consume them from a Python application. It includes:

- A Spring Boot application that provides a simple REST API.
- A Python script that makes HTTP requests to the Spring Boot API and returns the responses.

## Project Structure

- `spring-boot-app/`: Contains the Spring Boot application.
- `python-client/`: Contains the Python script to consume the REST API.

## How It Works

1. **Spring Boot Application**: 
   - Contains the necessary API endpoints at `http://localhost:8080/`.

2. **Python Script**: 
   - Predicts the price range using a trained model.

## API Documentation

### Base URL

`http://localhost:8080`

### Endpoints

#### 1. Get All Devices

- **Endpoint**: `/devices/`
- **Method**: `GET`
- **Description**: Retrieves all devices.
- **Response**:
  - **Status Code**: `200 OK`
  - **Body**: An array of device objects.

  ```json
  [
    {
      "id": 1,
      "battery_power": 842,
      "blue": 0,
      "clock_speed": 2.2,
      "dual_sim": 0,
      "fc": 1,
      "four_g": 0,
      "int_memory": 7,
      "m_dep": 0.6,
      "mobile_wt": 188,
      "n_cores": 2,
      "pc": 2,
      "px_height": 20,
      "px_width": 756,
      "ram": 2549,
      "sc_h": 9,
      "sc_w": 7,
      "talk_time": 19,
      "three_g": 0,
      "touch_screen": 0,
      "wifi": 1,
      "price_range": 1
    },
    ...
  ]

#### 2. Get Device by ID

- **Endpoint**: `/devices/{id}`
- **Method**: `GET`
- **Description**: Retrieves a specific device by its ID.
- **Path Parameter**:
  - `id` (String): The ID of the device.
- **Response**:
  - **Status Code**: `200 OK`
  - **Body**: A device object.

  ```json
  {
    "id": 1,
    "battery_power": 842,
    "blue": 0,
    "clock_speed": 2.2,
    "dual_sim": 0,
    "fc": 1,
    "four_g": 0,
    "int_memory": 7,
    "m_dep": 0.6,
    "mobile_wt": 188,
    "n_cores": 2,
    "pc": 2,
    "px_height": 20,
    "px_width": 756,
    "ram": 2549,
    "sc_h": 9,
    "sc_w": 7,
    "talk_time": 19,
    "three_g": 0,
    "touch_screen": 0,
    "wifi": 1,
    "price_range": 1
  }
- **Response (if device is not found)**:
  - **Status Code**: `404 NOT FOUND`
  - **Body**: An error message - Device not found.
  ```json
  {
    "status": 404,
    "error": "Not Found",
    "message": "Device not found"
  }
#### 3. Add a Device

- **Endpoint**: `/devices`
- **Method**: `POST`
- **Description**: Adds a new device to the database.
- **Request Body**: A device object (without the `id` field, which is auto-generated).

  ```json
  {
    "battery_power": 842,
    "blue": 0,
    "clock_speed": 2.2,
    "dual_sim": 0,
    "fc": 1,
    "four_g": 0,
    "int_memory": 7,
    "m_dep": 0.6,
    "mobile_wt": 188,
    "n_cores": 2,
    "pc": 2,
    "px_height": 20,
    "px_width": 756,
    "ram": 2549,
    "sc_h": 9,
    "sc_w": 7,
    "talk_time": 19,
    "three_g": 0,
    "touch_screen": 0,
    "wifi": 1
  }
- **Response**:
    - **Status Code**: `200 OK`
    - **Body**: The added device object (including the auto-generated `id` field).
    ```json
    {
      "id": 101,
      "battery_power": 842,
      "blue": 0,
      "clock_speed": 2.2,
      "dual_sim": 0,
      "fc": 1,
      "four_g": 0,
      "int_memory": 7,
      "m_dep": 0.6,
      "mobile_wt": 188,
      "n_cores": 2,
      "pc": 2,
      "px_height": 20,
      "px_width": 756,
      "ram": 2549,
      "sc_h": 9,
      "sc_w": 7,
      "talk_time": 19,
      "three_g": 0,
      "touch_screen": 0,
      "wifi": 1,
      "price_range": 0
    }
#### 4. Predict Device Price

- **Endpoint**: `/predict/{deviceId}`
- **Method**: `POST`
- **Description**: Predicts the price range for a device by its ID.
- **Path Parameter**:
  - `deviceId` (String): The ID of the device.
- **Response**:
  - **Status Code**: `200 OK`
  - **Body**: An integer representing the predicted price range.

  ```json
  2
- **Response (if device is not found)**:
    - **Status Code**: `404 NOT FOUND`
    - **Body**: An error message - Device not found.
    ```json
    {
        "status": 404,
        "error": "Not Found",
        "message": "Device not found"
    }
