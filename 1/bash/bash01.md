Enter 符号是CR  
cmd & ： 后台运行，关掉终端会停止运行   
nohup cmd & ： 后台运行，关掉终端不会停止运行
**临时添加环境变量PATH：**
export PATH=/usr/local/nginx/sbin/:$PATH，将/usr/local/nginx/sbin/目录临时添加到环境变量中
**当前用户永久添加环境变量：**
编辑.bashrc文件 vim ~/.bashrc  
文件末尾添加：export PATH="/usr/local/nginx/sbin/:$PATH"  
执行source ~/.bashrc
**所有用户永久添加环境变量：**
编辑/etc/profile文件 vim /etc/profile  
内容同上  
