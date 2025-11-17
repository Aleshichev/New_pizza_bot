## Pizza Shop Telegram Bot
A comprehensive Telegram bot for managing a coffee shop/café with product catalog, shopping cart, and order management features. Built with aiogram 3.x and PostgreSQL.
### Technology Stack
- Framework: aiogram 3.10.0 (Telegram Bot API)
- Database: PostgreSQL with SQLAlchemy 2.0 (async)
- Container: Docker & Docker Compose
- Language: Python 3.10+
- Dependencies: asyncpg, python-dotenv

## Features
### User Features
- Registration System: New users register with name and phone number
- Product Catalog: Browse products by categories (Coffee, Tea/Masala, Cocoa/Matcha, Drinks, Desserts, Additives)
- Shopping Cart: Add/remove items, adjust quantities
- Order Placement: Specify pickup time and submit orders
- Interactive Navigation: Inline keyboard navigation through menus

### Admin Features
- Product Management: Add, edit, and delete products
- Category Management: Organize products into categories
- Banner Management: Upload and update images for different pages
- Inventory Overview: View all products by category

```
├── app.py                      # Main application entry point
├── common/
│   ├── bot_commands.py        # Bot command definitions
│   ├── products.txt           # Product data template
│   └── texts_for_db.py        # Database initialization data
├── database/
│   ├── engine.py              # Database connection & initialization
│   ├── models.py              # SQLAlchemy models
│   └── orm_query/             # Database query functions
│       ├── banner.py
│       ├── cart.py
│       ├── category.py
│       ├── product.py
│       └── user.py
├── handlers/
│   ├── admin_private.py       # Admin command handlers
│   ├── user_private.py        # User command handlers
│   ├── user_group.py          # Group chat handlers
│   └── menu_processing.py     # Menu navigation logic
├── filters/
│   └── chat_types.py          # Custom filters for chat types
├── kbds/
│   ├── inline.py              # Inline keyboard layouts
│   └── reply.py               # Reply keyboard layouts
├── language/                   # Localization strings (Ukrainian)
├── middlewares/
│   └── db.py                  # Database session middleware
├── utils/
│   ├── paginator.py           # Pagination utility
│   └── order_message.py       # Order formatting
├── docker-compose.yml
├── Dockerfile
├── Makefile                   # Quick commands
└── pyproject.toml
```
## Database Schema
## Models

- Banner: Page banners with images and descriptions
- Category: Product categories
- Product: Products with name, description, price, image, category
- User: User profiles with contact information
- Cart: Shopping cart items linking users and products

#### Installation & Setup

- Docker and Docker Compose
- Telegram Bot Token from @BotFather
- Create a .env file in the root directory:
``` 
TOKEN=your_telegram_bot_token
DB_NAME=new_pizza_db
DB_PASSWORD=admin
DB_LOGIN=admin
DB_HOST=postgres
DB_PORT=5432
CHAT_GROUP_ID=your_chat_group_id  # For order notifications
```
#### Running with Docker
```
# Start PostgreSQL
make run
# Start the bot
make start
# View logs
make logs
# Stop services
make stop
# Remove containers
make down
# Rebuild and start
make build
```
### Key Features Implementation
**Pagination**  
Products and cart items use a custom paginator for easy navigation through large lists.  
**Inline Navigation**  
Multi-level menu system with breadcrumb navigation using callback data.  
**Localization**  
All user-facing text is in Ukrainian, organized in language/ directory for easy translation.  
**Session Management**  
SQLAlchemy async sessions managed via middleware for efficient database operations.  
**Admin Protection**  
Admin features are protected by group-based authorization using custom filters.  

**License**  
This project is provided as-is for educational purposes.  
**Contributors**  
Igor Aleshichev - Aleshichev.git@email.ua  
