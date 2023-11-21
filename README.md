# vendor_management

# Vendor Management System

This is a Vendor Management System developed using Django and Django REST Framework. The system handles vendor profiles, tracks purchase orders, and calculates vendor performance metrics.

## Setup Instructions

1. **Clone the Repository:**

    ```bash
 https://github.com/prudhvi-NHCL/vendor_management.git
    cd vendor-management-system
    ```

2. **Create a Virtual Environment:**

    ```bash
    python -m venv venv
    ```

3. **Activate the Virtual Environment:**

    - On Windows:

        ```bash
        .\venv\Scripts\activate
        ```

    - On macOS/Linux:

        ```bash
        source venv/bin/activate
        ```

4. **Install Dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

5. **Apply Migrations:**

    ```bash
    python manage.py migrate
    ```

6. **Run the Development Server:**

    ```bash
    python manage.py runserver
    ```

    The application will be accessible at [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

## API Endpoints

- **Vendor Management:**

    - Create a new vendor:

        ```bash
        http POST http://127.0.0.1:8000/api/vendors/ name="Vendor Name" contact_details="Contact Details" address="Vendor Address" vendor_code="V001"
        ```

    - List all vendors:

        ```bash
        http http://127.0.0.1:8000/api/vendors/
        ```

    - Retrieve a specific vendor's details:

        ```bash
        http http://127.0.0.1:8000/api/vendors/{vendor_id}/
        ```

    - Update a vendor's details:

        ```bash
        http PUT http://127.0.0.1:8000/api/vendors/{vendor_id}/ name="Updated Vendor Name"
        ```

    - Delete a vendor:

        ```bash
        http DELETE http://127.0.0.1:8000/api/vendors/{vendor_id}/
        ```

- **Purchase Order Management:**

    - Create a new purchase order:

        ```bash
        http POST http://127.0.0.1:8000/api/purchase_orders/ po_number="PO001" vendor={vendor_id} order_date="2023-01-01" delivery_date="2023-02-01" items='[{"name": "Item 1", "quantity": 10}]' quantity=10 status="pending"
        ```

    - List all purchase orders:

        ```bash
        http http://127.0.0.1:8000/api/purchase_orders/
        ```

    - Retrieve details of a specific purchase order:

        ```bash
        http http://127.0.0.1:8000/api/purchase_orders/{po_id}/
        ```

    - Update a purchase order:

        ```bash
        http PUT http://127.0.0.1:8000/api/purchase_orders/{po_id}/ status="completed"
        ```

    - Delete a purchase order:

        ```bash
        http DELETE http://127.0.0.1:8000/api/purchase_orders/{po_id}/
        ```

- **Vendor Performance Metrics:**

    - Retrieve a vendor's performance metrics:

        ```bash
        http http://127.0.0.1:8000/api/vendors/{vendor_id}/performance/
        ```

## Acknowledge Purchase Order

- While not explicitly detailed in the previous sections, use the following endpoint to acknowledge a purchase order:

    ```bash
    http POST http://127.0.0.1:8000/api/purchase_orders/{po_id}/acknowledge
    ```

    This endpoint will update acknowledgment_date and trigger the recalculation of average_response_time.

## Running Tests

Run tests to ensure the functionality of the application:

```bash
python manage.py test
