# slim

  #### `repo`
  * <https://github.com/104corp/104jb-c-slim3-proto>
  
#### `vagrant`
    //此為版本 2
    Vagrant.configure("2") do |config|
    
    //設定 load image 和 port mapping
    config.vm.box = "ubuntu/xenial64"
    config.vm.network "forwarded_port", guest: 80, host: 8080
    
    //設定目錄和權限
    config.vm.synced_folder ".", "/var/www/html/jobs/slim",
      :owner => "vagrant", :group => "vagrant",
      :mount_options => ["dmode=777,fmode=777"]
    config.vm.provider "virtualbox" do |vb|
    vb.memory = "1536"
    end
    
    //此行Specifies a shell command inline to execute 
    config.vm.provision "shell", inline: <<-SHELL
    
    //開始 shell 建立 相關套件  
     ..... install web server and configure
          
#### `composer`
       
#### `proto`
    DI
        
    log
        
    cache
        
    test
         
    swagger
        
    
  #### `CICD`
    