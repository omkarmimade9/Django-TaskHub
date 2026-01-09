# Django-TaskHub

A comprehensive task management and collaboration platform built with Django. Features include user authentication, team management, task creation with deadlines, priority levels, status tracking, file attachments, real-time comments, and activity logging. Perfect for teams to organize and collaborate on projects efficiently.

## Features

- **User Authentication**: Secure user registration and login
- **Team Management**: Create and manage teams with role-based access
- **Task Management**: Create, assign, and track tasks with deadlines
- **Priority Levels**: Mark tasks as high, medium, or low priority
- **Status Tracking**: Track task progress through different states
- **File Attachments**: Attach files and documents to tasks
- **Real-time Comments**: Comment on tasks with real-time updates
- **Activity Logging**: Comprehensive activity logs for audit trails
- **REST API**: Full-featured REST API with OpenAPI documentation
- **Async Tasks**: Background task processing with Celery

## Tech Stack

- **Backend**: Django 4.2+
- **API**: Django REST Framework
- **Database**: PostgreSQL
- **Cache & Queue**: Redis with Celery
- **Documentation**: drf-spectacular (Swagger/OpenAPI)
- **CORS**: django-cors-headers
- **Filtering**: django-filter
- **Server**: Gunicorn + Daphne (ASGI)

## Prerequisites

- Python 3.9+
- PostgreSQL 12+
- Redis 6+
- pip and virtualenv

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/omkarmimade9/Django-TaskHub.git
cd Django-TaskHub
```

### 2. Create Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables

```bash
cp .env.example .env
```

Edit `.env` with your configuration:

```env
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1

DB_NAME=taskhub_db
DB_USER=postgres
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=5432

CELERY_BROKER_URL=redis://localhost:6379/0
```

### 5. Database Setup

```bash
python manage.py migrate
python manage.py createsuperuser
python manage.py collectstatic --noinput
```

### 6. Run Development Server

```bash
python manage.py runserver
```

The API will be available at `http://localhost:8000/api/`

API Documentation: `http://localhost:8000/api/docs/`

## Running Celery (Optional)

For background task processing:

```bash
celery -A taskhub worker -l info
```

## Project Structure

```
Django-TaskHub/
├── taskhub/              # Main project settings
│   ├── settings.py      # Django settings
│   ├── urls.py          # URL routing
│   ├── asgi.py          # ASGI config
│   └── wsgi.py          # WSGI config
├── tasks/                # Tasks app
├── teams/                # Teams app
├── comments/             # Comments app
├── manage.py             # Django management script
├── requirements.txt      # Python dependencies
├── .env.example          # Environment variables template
└── README.md             # This file
```

## API Endpoints

### Tasks
- `GET /api/tasks/` - List all tasks
- `POST /api/tasks/` - Create new task
- `GET /api/tasks/{id}/` - Get task details
- `PUT /api/tasks/{id}/` - Update task
- `DELETE /api/tasks/{id}/` - Delete task

### Teams
- `GET /api/teams/` - List all teams
- `POST /api/teams/` - Create new team
- `GET /api/teams/{id}/` - Get team details
- `PUT /api/teams/{id}/` - Update team

### Comments
- `GET /api/comments/` - List all comments
- `POST /api/comments/` - Add comment
- `DELETE /api/comments/{id}/` - Delete comment

## Development

### Running Tests

```bash
python manage.py test
```

### Code Style

Use Black for code formatting:

```bash
pip install black
black .
```

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For issues and questions, please open an issue on GitHub.

## Author

Created with ❤️ by Omkar Mimade
