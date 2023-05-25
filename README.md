# URL_opener
This program will opean a particular link and then restart the app/software once the site is fully load
Also the user can provide the proxy information to change proxy
When the user will command the code as "Stop" the program will stop running
An auto proxy code comming soon

from selenium import webdriver
from selenium.webdriver.common.proxy import Proxy, ProxyType

def change_proxy_and_open_link(link, proxy_address):
    proxy = Proxy()
    proxy.proxy_type = ProxyType.MANUAL
    proxy.http_proxy = proxy_address
    proxy.ssl_proxy = proxy_address
    
    chrome_options = webdriver.ChromeOptions()
    chrome_options.add_argument('--proxy-server={}'.format(proxy_address))

    driver = webdriver.Chrome(options=chrome_options)
    
    driver.get(link)
    
	restart_application()

    driver.get(link)
    
    while True:
        user_input = input("Enter 'Stop' to exit: ")
        if user_input.lower() == "stop":
            break

    driver.quit()

link = input("Enter the link: ")
proxy_address = input("Enter the proxy address: ")

change_proxy_and_open_link(link, proxy_address)
