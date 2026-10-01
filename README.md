# StockVision

StockVision is a full-stack stock market analysis web application built with React, Spring Boot and PostgreSQL. It provides user authentication, live stock search and quote data, historical market data, and a virtual portfolio with buy and sell transactions.

## Current Features

- User registration and login
- Spring Security with JWT authentication
- BCrypt password hashing
- Protected application routes
- Live stock search
- Live stock quote data through Twelve Data
- Historical daily stock data
- Market charts and historical tables
- Virtual portfolio
- Portfolio holdings
- Virtual buy and sell transactions
- PostgreSQL persistence
- Layered backend architecture

## Technology Stack

### Frontend

- React
- Vite
- React Router
- Axios
- CSS

### Backend

- Java 21
- Spring Boot
- Spring Web
- Spring WebFlux WebClient
- Spring Data JPA
- Spring Security
- JWT
- PostgreSQL
- Maven

### External API

- Twelve Data

## Project Structure

```text
StockVision/
├── stock-market-frontend/
└── src/
    └── main/
        ├── java/com/stockmarket/
        │   └── analysis/
        │       ├── config/
        │       ├── controller/
        │       ├── dao/
        │       ├── dto/
        │       ├── entity/
        │       ├── enums/
        │       ├── exception/
        │       ├── repository/
        │       ├── security/
        │       └── service/
        └── resources/
            └── application.properties
```

## Backend Architecture

```text
React Frontend
      ↓
Controller
      ↓
Service
      ↓
DAO
      ↓
Repository
      ↓
PostgreSQL / Twelve Data
```

## Requirements

- Java 21
- Maven
- PostgreSQL
- Node.js and npm
- A Twelve Data API key

## Database Setup

Create a PostgreSQL database named:

```text
Stock_Market_Analysis
```

The application uses Hibernate with `ddl-auto=update`, so the required tables are created/updated from the entity mappings when the backend starts.

## Backend Configuration

The repository does not contain real passwords, JWT secrets or API keys.

Copy `src/main/resources/application.properties.example` as a reference and configure the required values using environment variables.

Required environment variables:

```text
DB_PASSWORD=your_postgresql_password
JWT_SECRET=your_long_random_secret
TWELVEDATA_API_KEY=your_twelve_data_api_key
```

Optional variables:

```text
DB_URL=jdbc:postgresql://localhost:5432/Stock_Market_Analysis
DB_USERNAME=postgres
JWT_EXPIRATION=86400000
FRONTEND_URL=http://localhost:5173
TWELVEDATA_BASE_URL=https://api.twelvedata.com
TWELVEDATA_EXCHANGE=NSE
```

Never commit real secrets to GitHub.

## Run Backend

From the backend project directory:

```bash
./mvnw spring-boot:run
```

On Windows:

```bash
mvnw.cmd spring-boot:run
```

The backend runs on:

```text
http://localhost:8080
```

## Run Frontend

Open a second terminal in `stock-market-frontend`:

```bash
npm install
npm run dev
```

Open the Vite URL shown in the terminal.

## Main API Endpoints

```text
POST /auth/register
POST /auth/login
GET  /stocks/search
GET  /stocks/{symbol}
GET  /stocks/{symbol}/history
GET  /portfolio
GET  /portfolio/holdings
GET  /portfolio/transactions
POST /portfolio/buy
POST /portfolio/sell
```

## Portfolio Note

The portfolio is virtual. Buy and sell actions are recorded by the application and do not place real-money orders with a stock broker.

## Market Data Note

Stock data is retrieved through Twelve Data. Availability, request limits and supported exchanges depend on the Twelve Data account and API plan.

## Future Scope

- Market overview and broader index analytics
- Dedicated stock analysis workspace
- Complete watchlist UI
- Stock screener
- Technical indicators
- Deeper portfolio analytics
- News and events
- Alerts and additional market analytics

## Security Note

Do not publish PostgreSQL passwords, Twelve Data API keys, JWT secrets or other credentials in source code or screenshots. If a credential has already been exposed, rotate it before making the repository public.
