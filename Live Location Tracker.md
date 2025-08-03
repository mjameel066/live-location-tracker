# Live Location Tracker

A family safety application that allows real-time location tracking and emergency alerts for family members.

## Features

- User registration and email verification
- Secure authentication system
- Real-time location tracking (coming soon)
- Family member management (coming soon)
- Emergency alerts (coming soon)
- Responsive web interface

## Technology Stack

- **Backend**: Flask (Python)
- **Database**: SQLite (development) / PostgreSQL (production)
- **Frontend**: HTML, CSS (Tailwind), JavaScript
- **Email**: Flask-Mail with Gmail SMTP
- **Deployment**: Railway

## Project Structure

```
live-location-tracker/
├── src/
│   ├── models/
│   │   ├── __init__.py
│   │   └── user.py          # User model and database schema
│   ├── routes/
│   │   ├── __init__.py
│   │   ├── auth.py          # Authentication routes
│   │   └── user.py          # User management routes
│   ├── static/
│   │   ├── index.html       # Main frontend application
│   │   ├── App.jsx          # React components (optional)
│   │   └── App.css          # Styles
│   ├── database/
│   │   └── .gitkeep         # Database directory
│   └── main.py              # Flask application entry point
├── requirements.txt         # Python dependencies
├── Procfile                 # Railway deployment configuration
├── railway.json             # Railway build configuration
├── .env.example             # Environment variables template
├── .gitignore               # Git ignore rules
└── README.md                # This file
```

## Local Development

### Prerequisites

- Python 3.11+
- pip (Python package manager)
- Git

### Installation

1. Clone the repository:
```bash
git clone <your-repository-url>
cd live-location-tracker
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up environment variables:
```bash
cp .env.example .env
# Edit .env with your configuration
```

4. Run the application:
```bash
python src/main.py
```

The application will be available at `http://localhost:5000`

### Environment Variables

Create a `.env` file with the following variables:

```env
SECRET_KEY=your-super-secret-key-here
FLASK_ENV=development
MAIL_USERNAME=youremail@gmail.com
MAIL_PASSWORD=your-gmail-app-password
MAIL_DEFAULT_SENDER=noreply@yourdomain.com
```

## Deployment

### Railway Deployment

1. **Prepare Gmail for Email Sending**
   - Enable 2-Factor Authentication on your Gmail account
   - Generate an App Password for the application
   - Save the App Password for Railway configuration

2. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial deployment"
   git push origin main
   ```

3. **Deploy on Railway**
   - Connect your GitHub repository to Railway
   - Set environment variables in Railway dashboard:
     - `SECRET_KEY`: A secure random string
     - `MAIL_USERNAME`: Your Gmail address
     - `MAIL_PASSWORD`: Gmail App Password
     - `MAIL_DEFAULT_SENDER`: Your sender email
     - `FLASK_ENV`: `production`

4. **Railway will automatically deploy using:**
   - `Procfile` for process configuration
   - `railway.json` for build settings
   - `requirements.txt` for dependencies

### Health Check

The application includes a health check endpoint at `/api/health` that Railway uses to monitor the application status.

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/resend-verification` - Resend verification email

### User Management
- `GET /api/users` - Get all users (admin)
- `GET /api/user/<id>` - Get specific user
- `PUT /api/user/<id>` - Update user information

### System
- `GET /api/health` - Health check endpoint

## Security Features

- Password hashing with Werkzeug
- Email verification for new accounts
- CORS protection
- SQL injection prevention with SQLAlchemy
- Secure session management

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License.

## Support

For support and questions, please contact the development team or create an issue in the repository.

