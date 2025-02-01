🚀 Laravel 11 CRUD Application

This project is a simple Product Management System built with Laravel 11. It demonstrates how to perform CRUD (Create, Read, Update, Delete) operations using Laravel's powerful features like migrations, controllers, models, and Blade templating. The application is styled with Bootstrap 5 and uses MySQL for the database.
🌟 Features

    Create Products: Add new products with a name and description.

    Read Products: View a paginated list of all products.

    Update Products: Edit existing product details.

    Delete Products: Remove products from the database.

    Form Validation: Validate input data before saving.

    Bootstrap 5: Modern and responsive design.

🛠️ Prerequisites

Before you begin, ensure you have the following installed:

    PHP (>= 8.1)

    Composer

    MySQL

    Laravel 11

🚀 Installation Steps
1. Clone the Repository
   ```git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name```
2. Install Dependencies
  ```composer install```
3. Set Up the Database

    Create a MySQL database.

    Update the .env file with your database credentials:
    ```DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=your_database_name
    DB_USERNAME=your_database_username
    DB_PASSWORD=your_database_password```
4. Run Migrations
   ```php artisan migrate```
5. Start the Development Server
   ```php artisan serve```
Visit the application in your browser:
  ```http://localhost:8000/products```
📂 Project Structure

    Migrations: Define the database schema for the products table.

    Models: Product.php handles data logic.

    Controllers: ProductController.php manages CRUD operations.

    Views: Blade templates for displaying and managing products.

    Routes: web.php defines the application routes.

🛠️ Key Files
Migration (create_products_table)
    ```Schema::create('products', function (Blueprint $table) {
          $table->id();
          $table->string('name');
          $table->text('detail');
          $table->timestamps();
      });```
Product Model (Product.php)
    ```protected $fillable = [
          'name',
          'detail',
      ];```

Product Controller (ProductController.php)
    ```public function index(): View
        {
            $products = Product::latest()->paginate(5);
            return view('products.index', compact('products'));
        }
        
        public function store(ProductStoreRequest $request): RedirectResponse
        {
            Product::create($request->validated());
            return redirect()->route('products.index')->with('success', 'Product created successfully.');
        } ```
Routes (web.php)
    ``` Route::resource('products', ProductController::class); ```
📝 License

This project is open-source and available under the MIT License.
🙏 Acknowledgments

    Laravel Documentation

    Bootstrap 5 Documentation

💡 How to Contribute

    Fork the repository.

    Create a new branch (git checkout -b feature/YourFeatureName).

    Commit your changes (git commit -m 'Add some feature').

    Push to the branch (git push origin feature/YourFeatureName).

    Open a pull request.

Enjoy building your Laravel CRUD application! If you have any questions or suggestions, feel free to open an issue or reach out. Happy coding! 🚀
