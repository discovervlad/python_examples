# Create certs
This example uses JWT token-based handshake with HTTPS:
* https://github.com/vimalloc/flask-jwt-extended
* https://blog.miguelgrinberg.com/post/running-your-flask-application-over-https

Prepare:
1. Use requirements.txt to install required packages
2. Create self-signed cert:
   openssl req -x509 -newkey rsa:4096 -nodes -out cert.pem -keyout key.pem -days 365
3. Start web service:
   python3 simple.py
4. Request JWT token
   curl --cacert cert.pem -H "Content-Type: application/json" --data @login.json https://127.0.0.1:5000/login
5. Add authorization header with bearer token to the new request and hit https://127.0.0.1:5000/protected
