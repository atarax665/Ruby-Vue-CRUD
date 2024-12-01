# Ruby + Vue CRUD Application

This is a simple CRUD (Create, Read, Update, Delete) application built with Ruby on Rails for the backend and Vue.js for the frontend.

## Features

- Create, read, update, and delete records
- RESTful API with Ruby on Rails
- Reactive frontend with Vue.js
- Simple and intuitive user interface

## Prerequisites

- Ruby (version 2.7 or later)
- Rails (version 6 or later)
- Node.js (version 12 or later)
- PostgreSQL (or any other preferred database)

## Getting Started

### Backend Setup

1. Clone the repository:

   ```sh
   git clone https://github.com/yourusername/ruby-vue-crud.git
   cd ruby-vue-crud
   ```

2. Install dependencies:

   ```sh
   bundle install
   ```

3. Set up the database:

   ```sh
   rails db:create
   rails db:migrate
   ```

4. Start the Rails server:
   ```sh
   rails server
   ```

### Frontend Setup

1. Navigate to the frontend directory:

   ```sh
   cd client
   ```

2. Install dependencies:

   ```sh
   npm install
   ```

3. Start the Vue development server:
   ```sh
   npm run dev
   ```

## Usage

- Open your browser and navigate to `http://localhost:3000` for the backend API.
- Navigate to `http://localhost:5173/` for the Vue.js frontend.

## Contributing

1. Fork the repository
2. Create a new branch (`git checkout -b feature-branch`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature-branch`)
5. Create a new Pull Request

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- Ruby on Rails
- Vue.js
- PostgreSQL
