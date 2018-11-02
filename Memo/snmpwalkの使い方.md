
# snmpwalkの使い方  

## 基本  

`snmpwalk -v [バージョン] -c [コミュニティ名] [IP or host名] [oid]`  

### 例  
#### localhostの全ての情報を確認  
`snmpwalk -v2 2c -c public localhost .`  

#### host名を確認  
`snmpwalk -v 2c -c public localhost .1.3.6.1.2.1.1.5` 
`snmpwalk -v 2c -c public localhost SNMPv2-MIB::sysName.0` 

#### IPアドレスを確認  
`snmpwalk -v 2c -c public localhost .1.3.6.1.2.1.4.20.1.1`  
`snmpwalk -v 2c -c public localhost IP-MIB::ipAdEntAddr`  

#### CPU使用率の確認  
`snmpwalk -v 2c -c public localhost .1.3.6.1.2.1.25.3.3.1.2`  
`snmpwalk -v 2c -c public localhost HOST-RESOURCES-MIB::hrProcessorLoad`  

#### メモリ容量の確認  
`snmpwalk -v 2c -c public localhost .1.3.6.1.4.1.2021.4.6`  
`snmpwalk -v 2c -c public localhost UCD-SNMP-MIB::memTotalReal`  
または  
`snmpwalk -v 2c -c public localhost .1.3.6.1.4.1.2021.4.6`  
`snmpwalk -v 2c -c public localhost UCD-SNMP-MIB::memAvailReal`  


## ipレンジで確認したい  
```
for((i=0;i<256;i++));
 do snmpwalk -v 2c -c public 10.0.0.$i .1.3.6.1.2.1.1.5;
done
```
