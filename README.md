# ONU DBm Checker with Web Panel

This project helps automate and simplify the process of checking ONU DBm values directly from a web interface without manual OLT login.

## Features
- Auto collect ONU optical info (Dbm values) from multiple OLTs (Huawei).
- Auto collect PPPoE active sessions from MikroTik routers.
- Match PPPoE Username with ONU MAC Address.
- Django based webpanel to search by PPPoE ID and view ONU DBm easily.
- Completely API-driven and database updated in real-time.

## Technologies Used
- Python (Paramiko, PyYAML, MySQL Connector, RouterOS API)
- Django (Web Framework)
- MySQL (Database)
- Cron Jobs (for Automation)

## Directory Structure

onu-dbm-checker/ ├── collector/ ├── onu_webpanel/ ├── webpanel/ ├── config.yaml ├── db_schema.sql ├── requirements.txt ├── manage.py


## Setup Instructions

1. Clone the repository
    ```bash
    git clone https://github.com/yourusername/onu-dbm-checker.git
    cd onu-dbm-checker
    ```

2. Install dependencies
    ```bash
    pip install -r requirements.txt
    ```

3. Set up the MySQL database
    ```bash
    mysql -u root -p < db_schema.sql
    ```

4. Edit the `config.yaml` with your OLT and MikroTik device credentials.

5. Run initial Django migrations
    ```bash
    python manage.py migrate
    ```

6. Start the Django server
    ```bash
    python manage.py runserver 0.0.0.0:8000
    ```

7. Setup Cron Jobs
    ```bash
    */5 * * * * /usr/bin/python3 /path/to/collector/olt_dbm_fetcher.py
    */5 * * * * /usr/bin/python3 /path/to/collector/mikrotik_pppoe_fetcher.py
    ```

8. Access the web panel
    ```
    http://your_server_ip:8000/search/
    ```

## Future Improvements
- Add user authentication for search panel.
- Multi-OLT Vendor Support (BDCOM, VSOL).
- ONT Authentication Status Monitoring.
- Real-time WebSocket Updates.

## License
MIT License
