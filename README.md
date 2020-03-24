```

一件安装python3
学习自动执行shell脚本


# the version of python
version="3.7.3"
# the installation directory of python
python3_install_dir="/data/lhadmin/app/python3"
tmp="tmp"

file_name="Python-$version.tgz"
sudo yum install libffi-devel -y
rm `pwd`"/$file_name"
wget "https://www.python.org/ftp/python/$version/$file_name"
mkdir $tmp
tar -xf $file_name -C $tmp
make_dir="$tmp/Python-$version"
cd $make_dir
if [ -d $python3_install_dir ]; then
  #sudo mv /usr/local/python3 /usr/local/python3`date +%Y%m%d`
  echo "目录存在,备份目录$python3_install_dir"
  mv  $python3_install_dir $python3_install_dir.`date '+%Y%m%d%H'`
fi
mkdir -p $python3_install_dir
./configure --prefix=$python3_install_dir --with-ssl
sudo make
sudo make install
echo "all in well !"
```
