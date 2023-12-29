```
import requests
import os
import bs4
from selenium import webdriver
from time import sleep
from selenium.webdriver.chrome.options import Options

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/34.0.1847.137 Safari/537.36 LBBROWSER'
}
# 创建保存音乐的文件夹
path = os.path.join('D:/Music')
if not os.path.exists(path):
    os.mkdir(path)
# 输入音乐名
name = input('请输入歌名：')
# 实现无可视化界面（固定写法）
chrome_options = Options()
chrome_options.add_argument('--headless')
chrome_options.add_argument('--disable-gpu')
# 初始化browser对象
# browser = webdriver.Chrome(executable_path='chromedriver.exe', chrome_options=chrome_options)
browser = webdriver.Chrome(options=chrome_options, executable_path='chromedriver.exe')


# 获取音乐的id、名字，歌手名
def get_id_name_singer(url):
    browser.get(url=url)
    browser.switch_to.frame('g_iframe')
    sleep(0.5)
    page_text = browser.execute_script("return document.documentElement.outerHTML")
    soup = bs4.BeautifulSoup(page_text, 'html.parser')
    music_ids = soup.select("div[class='td w0'] a")  # 音乐id
    music_id = music_ids[0].get("href")
    music_id = music_id.split('=')[-1]
    music_names = soup.select("div[class='td w0'] a b")  # 音乐名字
    music_name = music_names[0].get("title")
    music_singers = soup.select("div[class='td w1'] a")  # 歌手名
    music_singer = music_singers[0].string
    return music_id, music_name, music_singer


# 下载音乐
def download_music(url, song_name, singer):
    response = requests.get(url=url, headers=headers)
    music_data = response.content
    music_path_name = '{}_{}.mp3'.format(song_name, singer)
    music_path = path + music_path_name
    with open(music_path, 'wb') as f:
        f.write(music_data)
        print(music_path_name, '下载成功')


# 主函数
def main():
    url = 'https://music.163.com/#/search/m/?s=' + name + '&type=1'
    music_id, music_name, music_singer = get_id_name_singer(url)
    music_url = 'http://music.163.com/song/media/outer/url?id=' + music_id + '.mp3'
    download_music(music_url, music_name, music_singer)


if __name__ == '__main__':
    main()
    browser.quit()
```