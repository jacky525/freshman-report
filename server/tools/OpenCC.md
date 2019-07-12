# OpenCC

### PHP 簡繁體轉換

#### install OpenCC
     git clone https://github.com/BYVoid/OpenCC.git
     cd OpenCC
     make
     sudo make install
     
#### install opencc4php
     git clone [email protected]:NauxLiu/opencc4php.git
     cd opencc4php
     phpize
     ./configure
     make && sudo make install
     
#### test

     $od = opencc_open("s2twp.json"); //傳入配置檔名
     $text = opencc_convert("简体", $od);
     echo $text;
     opencc_close($od);
     
     //輸出  簡體