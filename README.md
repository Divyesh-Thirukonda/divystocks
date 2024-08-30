## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/Divyesh-Thirukonda/divystocks.git
    cd myportfolio
    ```

2. Create a virtual environment and activate it:
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. Install the required packages:
    ```sh
    pip install -r requirements.txt
    ```

4. Set up environment variables: Create a `.env` file in the root directory and add the following:
    ```env
    email=your_email
    password=your_password
    nytArticleAPI=your_nyt_api_key
    alphavantageapi=your_alphavantage_api_key
    twelveapi=your_twelve_api_key
    ```

5. Apply migrations:
    ```sh
    python manage.py migrate
    ```

6. Create a superuser:
    ```sh
    python manage.py createsuperuser
    ```

7. Run the development server:
    ```sh
    python manage.py runserver
    ```

## Usage

### Home Page
The home page displays:
- The latest NYT article titles, Forex data, and Top gainers and losers in the stock market.
- User's watchlist (if authenticated).

### Watchlist Management
Authenticated users can add or remove stocks from their watchlist using the following endpoints:
- Add to watchlist: `/add/<symbol>/`
- Remove from watchlist: `/remove/<symbol>/`
They can view the price, price change, and change percent. Watchlist should be sorted by change percent.

### Quote
Users can view more details (Price, EPS, EBITDA) about a stock using the search endpoint: `/quote/<symbol>/`
If an account exists, the user can add/remove from watchlist on this page

### Search
Users can search for specific stocks using the search endpoint: `/search/`

## Code Overview

### Views
- `home`: Fetches and displays projects, NYT article titles, forex data, top gainers and losers, and the user's watchlist.
- `quote_detail`: Displays detailed information about a specific stock.
- `add_to_watchlist`: Adds a stock to the user's watchlist.
- `remove_from_watchlist`: Removes a stock from the user's watchlist.
- `search`: Allows users to search for specific stocks.

### Models
- `ArticleTitle`: Stores the latest NYT article title.
- `UserProfile`: Manages the user's watchlist.

### Utilities
- `fetch_data.py`: Contains functions to fetch data from external APIs. Examples:
  - `fetch_nyt_article_title`: Fetches the latest NYT article titles.
  - `fetch_forex`: Fetches forex data.
  - `fetch_gainLose`: Fetches top gainers and losers in the stock market.

## Contributing
1. Fork the repository.
2. Create a new branch:
    ```sh
    git checkout -b feature-branch
    ```
3. Make your changes.
4. Commit your changes:
    ```sh
    git commit -am 'Add new feature'
    ```
5. Push to the branch:
    ```sh
    git push origin feature-branch
    ```
6. Create a new Pull Request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Contact
For any inquiries or issues, please contact [divyesh.thirukonda@gmail.com](mailto:divyesh.thirukonda@gmail.com).
