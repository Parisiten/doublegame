(在python虚拟环境中）

#创建数据库
mysql -uroot -pvagrant
create database doublegame default character set utf8 collate utf8_unicode_ci;
exit
show databases

#生成相关数据
cd doublegame
pip install -r requirements.txt
python manage.py migrate

#生成前端静态资源
cd frontend
npm install
npm run build

#软连接：
 cd backend
 删除其中的templates和static
 ln -s /home/xxx/codes/test1/frontend/dist templates
 ln -s /home/xxx/codes/test1/frontend/dist/static static
 #这里的"/home/xxx/codes/test1"应该是你的项目文件夹


#现在在doublegame执行runserver应该可以正常运行了

=====================================
代码规范设置为4空格
我们统一在JS和python的变量名使用小写字母加下划线
在HTML使用小写字母加减号
Vue单文件组件的名字使用大驼峰，组件的‘name’和HTML使用小写字母减号
在类前面使用'c_'标记
在函数前面使用'f_'标记
=====================================
如果使用pip安装新的插件，
安装完之后在项目文件夹（doublegame）中执行
  pip freeze > requirements.txt
把你安装的插件写入到requirements.txt这个清单中

如果使用npm安装新的插件,
在安装的时候记得使用 npm install --save [balabala....这里是插件名]
把你安装的插件写入到package.json这个清单中


每次安装使用新的插件在git提交时做说明
其他人根据最新的requirements.txt和package.json 来安装插件

  pip install -r requirements.txt

  npm install

======================================
如果你在前端要新建一些静态文件(js\html\css\图片)
如果和某一个vue组件有关的,放到frontend/src/assets里面,这里的文件会被webpack打包
如果和vue组件无关的,放到frontend/static,这里的文件生成时会直接被复制
