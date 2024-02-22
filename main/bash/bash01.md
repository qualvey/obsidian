Enter                                                   //符号是CR  

nohup cmd & ：                                //后台运行，关掉终端不会停止运行  

**临时环境变量P**  
export PATH=/usr/local/nginx/sbin/:$PATH
**用户永久环境变量：**  
vim ~/.bashrc                                                               // 编辑.bashrc文件 
export PATH="/usr/local/nginx/sbin/:$PATH"             // 添加内容
source ~/.bashrc                                                          //应用配置文件
**系统永久环境变量：**  
编辑/etc/profile文件 vim /etc/profile   

