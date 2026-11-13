#!/bin/bash
dnf install -y httpd

TOKEN=$(curl -s -X PUT "http://169.254.169.254/latest/api/token" \
  -H "X-aws-ec2-metadata-token-ttl-seconds: 300")
IID=$(curl -s -H "X-aws-ec2-metadata-token: $TOKEN" \
  http://169.254.169.254/latest/meta-data/instance-id)
AZ=$(curl -s -H "X-aws-ec2-metadata-token: $TOKEN" \
  http://169.254.169.254/latest/meta-data/placement/availability-zone)

cat > /var/www/html/index.html <<EOF
<!DOCTYPE html>
<html>
<head><title>HA App</title></head>
<body style="font-family:sans-serif;text-align:center;margin-top:80px">
  <h1>Highly Available Web App</h1>
  <p>Instance ID: <b>$IID</b></p>
  <p>Availability Zone: <b>$AZ</b></p>
</body>
</html>
EOF

echo "ok" > /var/www/html/health
systemctl enable --now httpd
