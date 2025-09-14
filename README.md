# Django Blog Application

A full-featured blog application built with Django that allows users to create accounts, write posts, and manage their profiles.

## Features

### User Management
- **User Registration**: New users can create accounts with a custom registration form
- **User Authentication**: Login and logout functionality
- **User Profiles**: Customizable user profiles with image upload capability
- **Profile Updates**: Users can update their personal information and profile pictures

### Blog Functionality
- **Post Creation**: Authenticated users can create new blog posts
- **Post Management**: Authors can edit and delete their own posts
- **Post Viewing**: 
  - Home page displays all posts with pagination (5 posts per page)
  - Individual post detail views
  - User-specific post listings
- **Post Ordering**: Posts are displayed with the most recent first
- **About Page**: Static page with application information

### Security Features
- **Authentication Required**: Post creation, editing, and deletion require user login
- **Author Verification**: Users can only edit/delete their own posts
- **Form Validation**: Custom forms with built-in validation

## Project Structure

The application consists of two main Django apps:

### Users App (`users/`)
Handles user authentication, registration, and profile management:

- **Views**:
  - `register()`: User registration with custom form
  - `logout_view()`: Custom logout functionality
  - `profile()`: Profile viewing and editing

- **Forms** (referenced):
  - `UserRegisterForm`: Custom user registration
  - `UserUpdateForm`: User information updates
  - `ProfileUpdateForm`: Profile information and image updates

### Blog App (`blog/`)
Manages blog posts and content:

- **Views**:
  - `home()`: Function-based view for homepage
  - `PostListView`: Class-based view for post listings with pagination
  - `UserPostListView`: Posts filtered by specific user
  - `PostDetailView`: Individual post details
  - `PostCreateView`: Create new posts (login required)
  - `PostUpdateView`: Edit existing posts (author only)
  - `PostDeleteView`: Delete posts (author only)
  - `about()`: Static about page

## Installation & Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd django-blog
   ```

2. **Create virtual environment**
   ```bash
   python -m venv blog_env
   source blog_env/bin/activate  # On Windows: blog_env\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install django
   pip install Pillow  # For image handling
   ```

4. **Database setup**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

5. **Create superuser** (optional)
   ```bash
   python manage.py createsuperuser
   ```

6. **Run the development server**
   ```bash
   python manage.py runserver
   ```

## Usage

### For Users
1. **Registration**: Visit `/register/` to create a new account
2. **Login**: Use Django's built-in authentication
3. **Create Posts**: After logging in, use the post creation form
4. **Manage Profile**: Update your profile information and upload a profile picture
5. **View Posts**: Browse all posts on the homepage or view posts by specific users

### For Developers
- **Templates**: The application uses Django templates located in respective app directories
- **Static Files**: CSS, JavaScript, and images should be placed in static directories
- **Media Files**: User uploads (profile pictures) are handled through Django's media handling
- **URL Configuration**: Each app should have its own `urls.py` for routing

## Key Features Explained

### Pagination
- Home page and user post pages display 5 posts per page
- Implemented using Django's built-in pagination

### Permission System
- Uses Django's `LoginRequiredMixin` for authentication
- `UserPassesTestMixin` ensures users can only modify their own posts
- Custom `test_func()` methods verify post ownership

### Form Handling
- Custom forms for user registration and profile updates
- File upload capability for profile pictures
- Form validation and error handling

### Class-Based vs Function-Based Views
- Mix of both approaches demonstrating Django flexibility
- Class-based views for CRUD operations
- Function-based views for simpler functionality

## Dependencies

- **Django**: Web framework
- **Pillow**: Python Imaging Library for image processing
- **Additional**: Any other dependencies should be listed in `requirements.txt`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

[Add your license information here]

## Support

For issues and questions, please [create an issue](link-to-issues) in the repository.
