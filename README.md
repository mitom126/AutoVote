import asyncio
import time
from pyppeteer import launch

async def main():
    browser = await launch(executablePath='C:\\Program Files (x86)\\Microsoft\\Edge\\Application\\msedge.exe', headless=False)
    page = await browser.newPage()
    await page.goto('https://dean1665.vn/svs2023/y-te-cham-soc-suc-khoe-cong-nghe-lam-dep/hand-of-hope-hoh-mo-hinh-gang-tay-robot-phuc-hoi-chuc-nang-van-dong-ban-tay-con-nguoi-603.html') #Vào trang dự án
    await page.click('a[onclick="cartorder(this)"]') #Click nút vào trang bình chọn
    await page.waitForNavigation({'waitUntil': 'networkidle2'})
    await asyncio.sleep(3)
    #Cho điểm 3 mục
    await page.select('select[name="score[603][1]"]', '5')
    await page.select('select[name="score[603][2]"]', '5')
    await page.select('select[name="score[603][3]"]', '5')
    #Điền tên và email
    await page.type('.form-control[name="fullname"]', 'test')
    await page.type('.form-control[name="email"]', 'test@thuvien247.vn')
    await asyncio.sleep(25)
    await browser.close()

asyncio.get_event_loop().run_until_complete(main())
