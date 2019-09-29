# Download the key
curl -sL https://repos.influxdata.com/influxdb.key | sudo apt-key add -

# Add the repo
echo "deb https://repos.influxdata.com/debian stretch stable" | sudo tee /etc/apt/sources.list.d/influxdb.list

# Update sources, install and start telegraf
sudo apt update && sudo apt install telegraf

sudo apt install hddtemp lm-sensors
sudo systemctl restart telegraf
