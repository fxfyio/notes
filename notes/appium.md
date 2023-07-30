- 安装：
  ```shell
  npm install -g appium
  ```
- 启动服务：
  ```shell
     appium
  ```
- 编写测试
  ```python
    from appium import webdriver
    import time
    from appium.webdriver.common.mobileby import MobileBy
    from selenium.webdriver.support.ui import WebDriverWait
    from selenium.webdriver.support import expected_conditions as EC

    desired_caps_1 = {
        'platformName': 'iOS',
        'platformVersion': '16.2',  # 你的 iOS 模拟器的版本
        'deviceName': 'iPhone 14 Pro Max',  # 你的 iOS 模拟器的设备名称
        'automationName': 'XCUITest',  # 使用的自动化测试工具
        'app': 'com.apple.Preferences',  # 要测试的应用的 bundle id
        'uuid': 'B4D56BCD-2CC7-4EF0-95DD-A713041A4379',
    }



    driver1 = webdriver.Remote('http://localhost:4724', desired_caps_1)

    def run(d, xpath):
        try:
            wait = WebDriverWait(d, 10)
            button = wait.until(EC.presence_of_element_located((MobileBy.XPATH, xpath)))
            button.click()
            
            retutn_xpath = '//XCUIElementTypeButton[@name="Settings"]'
            button_return =  wait.until(EC.presence_of_element_located((MobileBy.XPATH, retutn_xpath)))
            button_return.click()
        except Exception as e:
            print(f"\n💥 {xpath}: {e} 💥\n")

    xpath_list = [
        '//XCUIElementTypeCell[@name="Screen Time"]',
        '//XCUIElementTypeCell[@name="General"]',
        '//XCUIElementTypeCell[@name="Accessibility"]',
        '//XCUIElementTypeCell[@name="Safari"]',
        '//XCUIElementTypeCell[@name="News"]',
        '//XCUIElementTypeCell[@name="Translate"]',
        '//XCUIElementTypeCell[@name="Maps"]',
        '//XCUIElementTypeCell[@name="Shortcuts"]',
        '//XCUIElementTypeCell[@name="Health"]',
        '//XCUIElementTypeCell[@name="Siri & Search"]',
        '//XCUIElementTypeCell[@name="Photos"]',
        '//XCUIElementTypeCell[@name="Game Center"]',
        '//XCUIElementTypeCell[@name="Developer"]',
    ]

    def start(index = 0):
        xpath = xpath_list[index]
        run(driver1, xpath)
        next = index + 1
        if next < len(xpath_list):
            start(next)
        else:
            driver1.quit()

    start()

     
  ```