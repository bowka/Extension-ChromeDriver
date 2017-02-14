# Extension-ChromeDriver
##how to add local/chromeStore extension into chrome driver
 
FireFox use *.xpi
Chromedriver use *.crx 
 
withouth Shishito
 
 ```
 def start_browser(self):
    path = '/home/bowka/Salsita/letznav/LetzNav/player/build/letznav-player-0.1.0.crx'
    path_to_chromedriver = "/usr/bin/chromedriver"
    os.environ["webdriver.chrome.driver"] = path_to_chromedriver
    
    chrome_options = Options()
    chrome_options.add_extension(path)
    self.driver = webdriver.Chrome(executable_path=path_to_chromedriver, chrome_options=chrome_options)
```
        
 with Shishito
 shishito.py
 ```
 def get_browser_profile(self, browser_type, capabilities):
        if browser_type == 'chrome':
            profile = webdriver.ChromeOptions()
            profile.add_argument('--ignore-certificate-errors')
            if crx_path:
                self.add_extension_to_browser(profile, crx_path)
                ```
 
 ```
     def add_extension_to_browser(self, browser_profile, crx_path):
        """ Return browser profile updated with one or more extensions """

        browser_profile.add_extension(os.path.join(self.shishito_support.project_root, 'extension', crx_path))

        return browser_profile
        ```
        
