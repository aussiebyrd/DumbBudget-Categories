# DumbBudget

A simple, secure personal budgeting app with PIN protection. Track your income and expenses with a clean, modern interface.

This fork adds/changes extra categories for expenses to index.html.

![image](https://github.com/user-attachments/assets/7874b23a-159f-4c93-8e5d-521c18666547)


## Features

- 🔒 PIN-protected access
- 💰 Track income and expenses
- 📊 Real-time balance calculations
- 🏷️ Categorize transactions
- 📅 Date range filtering
- 🔄 Sort by date or amount
- 📱 Responsive design
- 🌓 Light/Dark theme
- 📤 Export to CSV
- 🔍 Filter transactions by type
- 💱 Multi-currency support

## Supported Currencies

DumbBudget supports the following currencies:
- USD (US Dollar) 🇺🇸
- EUR (Euro) 🇪🇺
- GBP (British Pound) 🇬🇧
- JPY (Japanese Yen) 🇯🇵
- AUD (Australian Dollar) 🇦🇺
- CAD (Canadian Dollar) 🇨🇦
- CHF (Swiss Franc) 🇨🇭
- CNY (Chinese Yuan) 🇨🇳
- HKD (Hong Kong Dollar) 🇭🇰
- NZD (New Zealand Dollar) 🇳🇿
- MXN (Mexican Peso) 🇲🇽
- RUB (Russian Ruble) 🇷🇺
- SGD (Singapore Dollar) 🇸🇬
- KRW (South Korean Won) 🇰🇷
- INR (Indian Rupee) 🇮🇳
- BRL (Brazilian Real) 🇧🇷
- ZAR (South African Rand) 🇿🇦
- TRY (Turkish Lira) 🇹🇷  
- PLN (Polish Złoty) 🇵🇱  
- SEK (Swedish Krona) 🇸🇪  
- NOK (Norwegian Krone) 🇳🇴  
- DKK (Danish Krone) 🇩🇰  
- IDR (Indonesia Rupiah) 🇮🇩

Set your preferred currency using the `CURRENCY` environment variable (defaults to USD if not set).

### Using Docker

```bash
docker run -d \
  -p 3000:3000 \
  -v /path/to/your/data:/app/data \
  -e DUMBBUDGET_PIN=12345 \
  -e CURRENCY=USD \
  -e BASE_URL=http://localhost:3000 \
  -e INSTANCE_NAME='My Account' \
  dumbwareio/dumbbudget:latest
```

### Using Docker Compose / Portainer (to build from GitHub)
services:
  dumbbudget:
    build:
      context: https://github.com/aussiebyrd/DumbBudget-Categories.git
    pull_policy: build
    container_name: DumbBudget
    ports:
      - 3005:3000
    volumes:
      - /srv/data/app-data/dumbbudget:/app/data
    environment:
      - DUMBBUDGET_PIN=##### #From 5 to 10 PIN numbers.
      - CURRENCY=AUD #Define preferrd currency here
      - BASE_URL=http://localhost:3005
    restart: on-failure:5
    
> **Note**: Replace `/path/to/your/data` with the actual path where you want to store your transaction data on the host machine.

### Environment Variables

| Variable | Description | Required | Default | Example |
|----------|-------------|----------|---------|---------|
| `DUMBBUDGET_PIN` | PIN code for accessing the application | Yes | - | `12345` |
| `PORT` | Port number for the server | No | `3000` | `8080` |
| `CURRENCY` | Currency code for transactions | No | `USD` | `EUR` |
| `BASE_URL` | Base URL for the application | No | `http://localhost:PORT` | `https://budget.example.com` |
| `INSTANCE_NAME` | Allows you to name each instance should you have multiple. | No | - | `My Account` |

## Development Setup

1. Clone the repository:
```bash
git clone https://github.com/DumbWareio/DumbBudget.git
cd DumbBudget
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file:
```env
DUMBBUDGET_PIN=12345
PORT=3000
NODE_ENV=development
BASE_URL=http://localhost:3000
CURRENCY=USD
INSTANCE_NAME='My Account'
```

4. Start the development server:
```bash
npm run dev
```

5. Open http://localhost:3000 in your browser

## Building from Source

```bash
# Build the Docker image
docker build -t dumbwareio/dumbbudget:latest .

# Create a directory for persistent data
mkdir -p ~/dumbbudget-data

# Run the container
docker run -d \
  -p 3000:3000 \
  -v ~/dumbbudget-data:/app/data \
  -e DUMBBUDGET_PIN=12345 \
  -e BASE_URL=http://localhost:3000 \
  -e INSTANCE_NAME='My Account' \
  dumbwareio/dumbbudget:latest
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Security

DumbBudget includes several security features:
- PIN protection for access
- Rate limiting on PIN attempts
- Temporary lockout after failed attempts
- No sensitive data stored in browser storage
- Secure session handling

## Support

- Report bugs by opening an issue
- Request features through issues
- [Join our community discussions](https://discord.gg/zJutzxWyq2)

## Support the Project

<a href="https://www.buymeacoffee.com/dumbware" target="_blank">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="60">
</a>

---
Made with ❤️ by [DumbWare.io](https://github.com/DumbWareio)
