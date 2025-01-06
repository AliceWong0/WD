<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ABC Shop</title>
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        .navbar {
            background-color: #17a2b8;
        }

        .navbar-brand img {
            width: 40px;
            height: 40px;
            border-radius: 50%; 
        }

        .search-bar {
            display: flex;
            justify-content: flex-end;
            align-items: center;
        }

        .search-bar input[type="text"] {
            width: 200px; 
            margin-right: 10px;
        }

        .product-card {
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 15px;
            text-align: center;
            margin: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .product-card img {
            max-width: 100%;
            height: auto;
            margin-bottom: 10px;
        }

        .product-card h5 {
            font-size: 1.2rem;
            margin-bottom: 10px;
        }

        .add-to-cart {
            background-color: #dc3545;
            color: #fff;
            border: none;
            padding: 10px 15px;
            border-radius: 3px;
            cursor: pointer;
        }

        .add-to-cart:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    
    <nav class="navbar navbar-expand-lg navbar-light">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">
            <img src="ABC.jpg" alt="">
                ABC Shop
            </a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav me-auto">
                    <li class="nav-item"><a class="nav-link" href="#">Home</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Product</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Services</a></li>
                    <a class="nav-link" href="#">Cart <span class="badge bg-danger rounded-circle">3</span></a>
                    
                </ul>
                
                <form method="GET" action="{{ url('search') }}" class="search-bar d-flex">
                    <input type="text" name="query" class="form-control" placeholder="Search for products">
                    <button type="submit" class="btn btn-success">Search</button>
                </form>
                
                
            </div>
        </div>
    </nav>

    <div class="container my-4">
       
        <div class="row">
            @if(isset($products) && $products->count() > 0)
                @foreach ($products as $product)
                    <div class="col-md-4">
                        <div class="product-card">
                            <img src="A001.jpg" class="img-fluid" alt="Product Image">
                            <h5>{{ $product->product_name }}</h5>
                            <p><strong>RM {{ number_format($product->price, 2) }}</strong></p>
                            <button class="add-to-cart">Add to Cart</button>
                        </div>
                    </div>
                @endforeach
            @else
                <p class="text-center">No products found.</p>
            @endif
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
