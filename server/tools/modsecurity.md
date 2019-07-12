# modsecurity

#### `Reference`
    * <https://modsecurity.org/>
    * [安裝](https://modsecurity.org/download.html)
  
        #  sudo mv /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf
        #  sudo vi /etc/modsecurity/modsecurity.conf
           modify 
           SecRuleEngine On
        
        #  sudo systemctl restart apache2

#### `OWASP ModSecurity CRS`
 
  * 參考
  
    <https://github.com/SpiderLabs/owasp-modsecurity-crs>
  
####  `Write A WAF Rule` 

    #  sudo vi /etc/modsecurity/modsecurity.conf
    // 可以寫在這裡，新增 ip免檢查 rule
    // 拆分為兩行，請使用 反斜號 \
     
    // id：101 - 分配給此規則的唯一ID。
    // 階段：1 - 將規則（或鏈）置於階段1處理中。有5個階段，包括請求標題（1），請求主體（2），響應標題（3），響應主體（4）和日誌記錄（5）。
    // t：none - 表示在匹配之前不使用任何操作來轉換規則中使用的變量的值。例如t：utf8toUnicode將所有UTF-8字符序列轉換為Unicode以協助輸入規範化。
    // nolog - 防止規則匹配出現在錯誤和審計日誌中。
    // pass - 儘管匹配成功，仍繼續使用下一個規則進行處理。
    // ctl：ruleEngine = off - 此操作在瞬態，每個事務的基礎上更改ModSecurity配置。這將僅影響執行操作的事務。在這種情況下，ModSecurity規則引擎已關閉。
    
    SecRule REMOTE_ADDR  "@ipMatch 10.0.2.2" \
    "id:102,phase:1,t:none,nolog,pass,ctl:ruleEngine=off"
    
    #  sudo systemctl restart apache2

####  `log` 
    #  cd /var/log/apache2/

    /var/log/apache2/error.log
    
    
    [Thu Jul 11 10:20:08.250294 2019] [:error] [pid 10833] [client 10.0.2.2:60578] [client 10.0.2.2] 
    ModSecurity: Warning. Operator GE matched 5 at TX:inbound_anomaly_score. 
    [file "/usr/share/modsecurity-crs/rules/RESPONSE-980-CORRELATION.conf"] [line "86"] 
    [id "980130"] [msg "Inbound Anomaly Score Exceeded (Total Inbound Score: 5 - SQLI=0,XSS=0,RFI=0,LFI=0,RCE=5,PHPI=0,HTTP=0,SESS=0): 
    Remote Command Execution: Unix Shell Code Found; individual paranoia level scores: 5, 0, 0, 0"] 
    [tag "event-correlation"] [hostname "localhost"] [uri "/"] [unique_id "XScNWH8AAQEAACpReLcAAAAA"]
    
    
    /var/log/apache2/modsec_audit.log
    
    --c4322f4b-H--
    Message: Warning. Matched phrase "bin/bash" at ARGS:exec. [file "/usr/share/modsecurity-crs/rules/REQUEST-932-APPLICATION-ATTACK-RCE.conf"] [line "503"] [id "932160"] [msg "Remote Command Execution: Unix Shell Code Found"] [data "Matched Data: bin/bash found within ARGS:exec: /bin/bash"] [severity "CRITICAL"] [ver "OWASP_CRS/3.1.1"] [tag "application-multi"] [tag "language-shell"] [tag "platform-unix"] [tag "attack-rce"] [tag "OWASP_CRS/WEB_ATTACK/COMMAND_INJECTION"] [tag "WASCTC/WASC-31"] [tag "OWASP_TOP_10/A1"] [tag "PCI/6.5.2"]
    Message: Access denied with code 403 (phase 2). Operator GE matched 5 at TX:anomaly_score. [file "/usr/share/modsecurity-crs/rules/REQUEST-949-BLOCKING-EVALUATION.conf"] [line "93"] [id "949110"] [msg "Inbound Anomaly Score Exceeded (Total Score: 5)"] [severity "CRITICAL"] [tag "application-multi"] [tag "language-multi"] [tag "platform-multi"] [tag "attack-generic"]
    Message: Warning. Operator GE matched 5 at TX:inbound_anomaly_score. [file "/usr/share/modsecurity-crs/rules/RESPONSE-980-CORRELATION.conf"] [line "86"] [id "980130"] [msg "Inbound Anomaly Score Exceeded (Total Inbound Score: 5 - SQLI=0,XSS=0,RFI=0,LFI=0,RCE=5,PHPI=0,HTTP=0,SESS=0): Remote Command Execution: Unix Shell Code Found; individual paranoia level scores: 5, 0, 0, 0"] [tag "event-correlation"]
    Apache-Error: [file "apache2_util.c"] [line 273] [level 3] [client 10.0.2.2] ModSecurity: Warning. Matched phrase "bin/bash" at ARGS:exec. [file "/usr/share/modsecurity-crs/rules/REQUEST-932-APPLICATION-ATTACK-RCE.conf"] [line "503"] [id "932160"] [msg "Remote Command Execution: Unix Shell Code Found"] [data "Matched Data: bin/bash found within ARGS:exec: /bin/bash"] [severity "CRITICAL"] [ver "OWASP_CRS/3.1.1"] [tag "application-multi"] [tag "language-shell"] [tag "platform-unix"] [tag "attack-rce"] [tag "OWASP_CRS/WEB_ATTACK/COMMAND_INJECTION"] [tag "WASCTC/WASC-31"] [tag "OWASP_TOP_10/A1"] [tag "PCI/6.5.2"] [hostname "localhost"] [uri "/"] [unique_id "XScNWH8AAQEAACpReLcAAAAA"]
    Apache-Error: [file "apache2_util.c"] [line 273] [level 3] [client 10.0.2.2] ModSecurity: Access denied with code 403 (phase 2). Operator GE matched 5 at TX:anomaly_score. [file "/usr/share/modsecurity-crs/rules/REQUEST-949-BLOCKING-EVALUATION.conf"] [line "93"] [id "949110"] [msg "Inbound Anomaly Score Exceeded (Total Score: 5)"] [severity "CRITICAL"] [tag "application-multi"] [tag "language-multi"] [tag "platform-multi"] [tag "attack-generic"] [hostname "localhost"] [uri "/"] [unique_id "XScNWH8AAQEAACpReLcAAAAA"]
    Apache-Error: [file "apache2_util.c"] [line 273] [level 3] [client 10.0.2.2] ModSecurity: Warning. Operator GE matched 5 at TX:inbound_anomaly_score. [file "/usr/share/modsecurity-crs/rules/RESPONSE-980-CORRELATION.conf"] [line "86"] [id "980130"] [msg "Inbound Anomaly Score Exceeded (Total Inbound Score: 5 - SQLI=0,XSS=0,RFI=0,LFI=0,RCE=5,PHPI=0,HTTP=0,SESS=0): Remote Command Execution: Unix Shell Code Found; individual paranoia level scores: 5, 0, 0, 0"] [tag "event-correlation"] [hostname "localhost"] [uri "/"] [unique_id "XScNWH8AAQEAACpReLcAAAAA"]
    Action: Intercepted (phase 2)
    Stopwatch: 1562840408243719 6858 (- - -)
    Stopwatch2: 1562840408243719 6858; combined=5028, p1=694, p2=4095, p3=0, p4=0, p5=239, sr=65, sw=0, l=0, gc=0
    Response-Body-Transformed: Dechunked
    Producer: ModSecurity for Apache/2.9.3 (http://www.modsecurity.org/); OWASP_CRS/3.1.1.
    Server: Apache/2.4.18 (Ubuntu)
    Engine-Mode: "ENABLED"
    
    --c4322f4b-Z--