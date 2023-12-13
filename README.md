
# 🚀 Microservices Architecture with RabbitMQ, Redis, and Symfony PHP

## Overview

This project showcases a sophisticated microservices architecture, utilizing Symfony PHP for each microservice, RabbitMQ as a dynamic message broker, and Redis for efficient caching. The architecture comprises two pivotal Symfony microservices: User & Event Microservice and Betting Microservice. RabbitMQ orchestrates asynchronous communication between these microservices, while Redis optimizes data retrieval speed, enhancing overall performance and mitigating database load.

## 🛠️ Components

1. **User & Event Microservice:**
   - Manages user data and sports events using Symfony PHP.
   - Publishes user-related events (e.g., customization) and sports events data.
   - Leverages Redis for caching frequently accessed user data and sports events.

2. **Betting Microservice:**
   - Handles betting-related data using Symfony PHP.
   - Consumes user-related events and sports events data, then publishes betting data.
   - Takes advantage of Redis for caching frequently accessed betting-related data.

3. **RabbitMQ:**
   - Serves as a dynamic message broker between the User & Event Microservice and Betting Microservice.
   - Facilitates seamless asynchronous communication.

4. **Redis:**
   - Employs caching for frequently accessed data within the User & Event Microservice and Betting Microservice.
   - Enhances data retrieval speed and reduces the load on databases.

## 🌐 Diagram Overview

```plaintext
+----------------------+          +----------------------+
|   User & Event       |          |   Betting            |
|   Microservice       |          |   Microservice       |
+-----------^----------+          +----------^-----------+
            |                                |
            | Publishes events, user data    |
            |                                |
            v                                v
+---------------------+      +-----------------------------+
|      Redis Cache    |      |        Redis Cache         |
|                     |      |                            |
+---------------------+      +-----------------------------+
            |                                |
            | Caches user and sports events   |
            | data                           |
            |                                |
+-----------+--------------------------------+------------------+
|                  RabbitMQ Message Queue                        |
+----------------------------------------------------------------+
            |
            | Consumes events, user data, and publishes betting data
            |
+-----------v----------+          +-----------------------------+
|      User Entity    |          |        Bet & Trend Entity   |
|      Event Entity   |          |                             |
+---------------------+          +-----------------------------+
```

## 🚀 Usage

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/your-repo.git
   ```

2. **Install Dependencies:**
   - Navigate to each Symfony microservice directory and run:
     ```bash
     composer install
     ```

3. **Configure RabbitMQ and Redis:**
   - Update configuration files in each Symfony microservice to point to your RabbitMQ and Redis instances.

4. **Run Microservices:**
   - Start each Symfony microservice:
     ```bash
     php bin/console server:start
     ```

## ⚙️ Configuration

- Adjust Symfony configuration files (config/packages/*.yaml) in each microservice to set environment-specific variables for RabbitMQ and Redis connections.

## 🤝 Contributions

Contributions are welcome! Please follow our [Contribution Guidelines](CONTRIBUTING.md).

## 📝 License

This project is licensed under the [MIT License](LICENSE).
