# AutoVote
1 công cụ được tạo nên để spam vote =))) 
import asyncio
import time
from pyppeteer import launch
#vào trang bình chọn
async def main():
    browser = await launch(executablePath='D:\\p\\chrome.exe', headless=False)
    page = await browser.newPage()
    await page.goto('https://dean1665.vn/svs2023/y-te-cham-soc-suc-khoe-cong-nghe-lam-dep/hand-of-hope-hoh-mo-hinh-gang-tay-robot-phuc-hoi-chuc-nang-van-dong-ban-tay-con-nguoi-603.html')
    await page.click('a[onclick="cartorder(this)"]')
    await page.waitForNavigation({'waitUntil': 'networkidle2'})
    await asyncio.sleep(10)
    await browser.close()

asyncio.get_event_loop().run_until_complete(main())
