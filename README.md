
# Flight Price Monitoring pipeline

## Purpose
This project provides a flight price monitoring system using various tools such as Apache Kafka, MinIO, MongoDB, Amadeus API, and Telegram Bot. The system checks for price updates on flight offers and notifies users about price changes. The core functionality is implemented in Python, and Docker is used for containerization. This project reads flight data from Kafka, monitors prices using the Amadeus API, stores data in MongoDB, and communicates with users via a Telegram bot.

## MinIO Buckets
In order to successfully run this system, you need to create the following buckets on your MinIO server:

- `my-amadeus`: The bucket where flight data will be uploaded to.
- `zip`: The destination bucket where the zip archive containing the flight data will be stored after the daily archive operation.

## Requirements
Before running the program, make sure you have the following installed:

1. **Docker**: You need Docker to run the application in containers.
2. **Docker Compose**: Docker Compose is used to configure and manage multiple containers.
3. **Python 3.x**: The system is implemented in Python, and you should have Python 3.x installed.
4. **MinIO**: MinIO is used as the object storage system.
5. **Kafka**: Apache Kafka is used for messaging.
6. **MongoDB**: MongoDB is used to store flight request data.
7. **Telegram Bot API Token**: You will need to create a Telegram bot and obtain a token.

### Python Requirements
The following Python libraries are required:
- `requests`
- `pymongo`
- `telebot`
- `boto3`
- `pyspark`

These can be installed using `pip`:

```bash
pip install requests pymongo telebot boto3 pyspark
```

## How to Create a Telegram Bot with BotFather

Follow these steps to create your own Telegram bot and get the bot token:

1. Open Telegram and search for `@BotFather`.
2. Start a conversation with BotFather and type `/newbot`.
3. Follow the instructions to set up the bot, including giving it a name and a username.
4. After the bot is created, BotFather will give you an API token. This token will be used to interact with the Telegram Bot API.

### Adding the Telegram Bot Token to the Script

1. Copy the token you received from BotFather.
2. Open the `price_check.py` script.
3. Locate the line where the `TOKEN` variable is defined, and paste your token in place of the existing value:

```python
TOKEN = "your-bot-token-here"
```

## Docker Setup

The application uses Docker to run all components in isolated containers. A `docker-compose.yaml` file is included in the repository to set up the necessary services.

### Running the Application with Docker

1. Clone the repository from GitHub.
2. Navigate to the project directory where `docker-compose.yaml` is located.
3. Build and start the services by running the following command:

```bash
docker-compose up --build
```

This will start all the required containers (MinIO, MongoDB, Kafka, and others) and make the system fully functional.