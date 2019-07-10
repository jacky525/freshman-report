# slim 3 + DI6

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
          
#### `proto`
    
      * DI          "php-di/slim-bridge"
        
      * config      "symfony/dotenv"
            parse config and set to env
        
      * template    "slim/twig-view"
            
      * log         "104corp/jblog"
            
      * cache       "symfony/cache"
            
      * test          "codeception/codeception"
            configure codeception.yml
            // init
            php vendor/bin/codecept bootstrap
            // generate test case
            php vendor/bin/codecept generate:cest acceptance First
            // run test
            php vendor/bin/codecept run
            
      * code style    "squizlabs/php_codesniffer"
            configure phpcs.xml 
            php vendor/bin/phpcs
            
      * swagger     "zircote/swagger-php" 
            vendor/bin/openapi app/ --output ${SWAGGER_FILE}
            
  #### `CICD`
    
      * Travis CI
            configure .travis.yml
      * install awscli
            - pip install --user awscli 
      * AWS
            IAM
                create user 
                create Roles
                    for ec2
                        - AWSCodeDeployFullAccess
                        - AmazonS3ReadOnlyAccess
                    for codedeploy
                        - AWSCodeDeployRole
                create Policies 
            S3 
                create S3
            EC2 
                create EC2
            Tools
                create CodeDeploy 
      ec2 machine 
            install codedeploy agent           
      * AWS CodeDeploy
            appspec.yml
