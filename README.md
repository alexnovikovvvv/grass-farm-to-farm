### GRASS + Proxy Seller residential proxies | With 10% author royalty!

# Install Python *(required)

### For Windows/Mac/Linux
It is recommended to use **Python 3.10**.  
[Download Python 3.10 here](https://www.python.org/downloads/release/python-3100/).

### For Android OS

Run the following commands:

```bash
pkg update && upgrade
pkg install tur-repo
pkg install python-is-python3.10
pkg install -y rust binutils
CARGO_BUILD_TARGET="$(rustc -Vv | grep "host" | awk '{print $2}')" pip install maturin
```

# Install Requirements *(required)

Run the following command to install the necessary packages:

```bash
pip install -r requirements.txt
```

# How to Get GRASS User ID *(required)

## For Windows/Mac/Linux
1. Open your browser and login to the GRASS dashboard.
2. Press `F12` to open the **Inspect Elements** panel.
3. Go to the **Console** tab and paste the following code:

   ```javascript
   localStorage.getItem('userId')
   ```

4. You will receive your user ID, which looks like this: `"32d23d23d32d2........"`
5. If you can't paste, type allow pasting and press Enter, then paste the line above.
6. Paste your the Grass User ID inside user_id.txt and save file.

## For Android OS

1. Download and install [Kiwi Browser](https://play.google.com/store/apps/details?id=com.kiwibrowser.browser&hl=en).
2. Login to the GRASS web and go to the dashboard.
3. Open the **Developer Tools** in the Kiwi browser.
4. Go to the **Console** tab and paste this code:

   ```javascript
   localStorage.getItem('userId')
   ```

5. If you can't paste, type `allow pasting` and press Enter, then paste the line above.

# Running the Script

## For Windows/Mac/Linux

You can use simple console, but if you have multiple accounts and you need to full authomation your solution here [PM2](https://pm2.keymetrics.io/docs/usage/quick-start/)

### How to run

Change proxy_seller_api_key.txt file and paste your API Key. Check this [API KEY](https://proxy-seller.io/personal/api/)

*Also you need to paste your IP Adress to second field on this page (below API key field) and press the Save button after your can launch script.py script.

```bash
python script.py
```

The script.py use the proxy seller API for authomation work.

**Example error logs:
"No API Key found in 'proxy_seller_api_key.txt'." - need to check the Proxy Seller API Key inside proxy_seller_api_key.txt file<br />
"Error: 'proxy_seller_api_key.txt' file not found." - need to check proxy_seller_api_key.txt file<br />
"PS: package status: False" - need to check availble traffic on Proxy Seller<br />
"Error delete proxy list: ..." - just skip, not required<br />
"Error create proxy list: ..." - proxy-seller troubles. Just try after few minutes<br />
"PS: No proxies found" - proxy-seller troubles. Just try after few minutes<br />
"Error download proxy list: ..." - proxy-seller troubles. Just try after few minutes<br />
"No user ID found in 'user_id.txt'." - need to check the GRASS ID inside user_id.txt file<br />
"Error: 'user_id.txt' file not found." - need to check user_id.txt file<br />
"Error with proxy ...: ..." - sometimes the proxy address not working and this proxy added to proxy cache for exclude from proxy list. This need for exclude redundant work. After restart sessing we will use full proxy list.

## For Android OS

Configure Termux

After installing Termux, ensure you have allowed storage permission for Termux (device app) settings.  
Alternatively, run this command in Termux:

```bash
termux-setup-storage
```

#### Using [PM2](https://pm2.keymetrics.io/docs/usage/quick-start/) (not required)

Install [NPM](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

Install PM2

```bash
$ npm install pm2@latest -g
```

Launch script

```bash
$ pm2 start script.py --name script1-account-1 --no-autorestart
```

Launch script with periodic restart every three hours

```bash
$ pm2 start script.py --name script-account-1 --cron-restart="0 */3 * * *"
```

Save PM2 config

```bash
$ pm2 save
```

Relaunch scripts after restart PC (before restart need to save config)

```bash
$ pm2 update
```

Stop script

```bash
$ pm2 stop all
```
or

```bash
$ pm2 stop script1
```
