<h1 align="center">ð Git ä½¿ç¨å©æ PowerShell ç</h1>

<p  align="center">
    <a href="https://github.com/sumisos/gh" target="_blank"><img src="https://img.shields.io/badge/sumisos-gh-blue?logo=github" alt="Github Repository" /></a>
    <a href="https://github.com/sumisos/gh/blob/main/LICENSE" target="_blank"><img src="https://img.shields.io/badge/License-MIT-green" alt="Package License" /></a>
    <a href="https://github.com/sumisos/gh/tags" target="_blank"><img src="https://img.shields.io/github/v/tag/sumisos/gh?label=Version" alt="Release Version" /></a>
</p>

## å®è£
```bash
$ git submodule add http://github.com/sumisos/gh.git
```

## ç¨æ³
* åæ¬¡è¿è¡ä¼èªå¨çæéç½®æä»¶ï¼`.env`ï¼  
* å¯ä»¥æå¯å¨èæ¬ç§»å°ä¸å±ç®å½ä½¿ç¨ï¼ä½åªæ¯æç§»åºä¸å±ï¼  

```
Your-Project/
 âââ .git/       # Git ä»åºä¿¡æ¯
 âââ gh/
 â âââ .env      # éç½®æä»¶
 â âââ core.ps1  # æ ¸å¿åè½å®ç°èæ¬
 â âââ ci.ps1    # å¯å¨èæ¬
 â âââ ...
 âââ ...         # ä½ çé¡¹ç®æä»¶
```

åæï¼  
```
Your-Project/
 âââ .git/       # Git ä»åºä¿¡æ¯
 âââ gh/
 â âââ .env      # éç½®æä»¶
 â âââ core.ps1  # æ ¸å¿åè½å®ç°èæ¬
 â âââ ci.ps1    # å¯å¨èæ¬
 â âââ ...
 âââ ci.ps1      # å¯å¨èæ¬æ·è´
 âââ ...         # ä½ çé¡¹ç®æä»¶
```

å¦æ­¤ä¸æ¥ï¼ä¹åææç `.\gh\ci.ps1` => `.\ci.ps1`ãï¼èä¸ä¸¤ç§æ¹å¼é½è½ä½¿ç¨ï¼  

å¹¶ä¸ä»¥åå½çæ¬æ´æ°æ¶ï¼ä¹ä¸éè¦éæ°æ·è´å¯å¨èæ¬ï¼å¯ä»¥ç»§ç»­æ²¿ç¨ã  
å ä¸º**ä¸è¬æ¥è¯´**å¥å£æä»¶æ¯ä¸ä¼åå¨çã  

### éç½®æä»¶ `.env`
```
COMMAND_SAVE=save  # save åè½çå«å
COMMAND_DIST=dist  # dist åè½çå«å
BRANCH_MAIN=main   # èä»åºæ¯master åæ¥Githubææ¿æ²»æ­£ç¡®åºé¤äº"å¥´é¶å¶"  Code Lives Matter!
AUTO_DELETE=       # **æç¨** èªå¨å é¤ç®å½ çç©ºä¸ºä¸å é¤
ENABLE_GITLAB=     # å¤ä»åºåå­ éè¦æåéç½®å¥½å¤è¿ç¨ä»åº
DEBUG=false        # å¼å¯Debugæ¨¡å¼ æå°åºåæ¬åºè¯¥è¿è¡çå½ä»¤
```

> å¦æåè<a href="https://ews.ink/tech/git-github-gitee" target="_blank">åæ¶ä½¿ç¨ Github ä»¥å Gitee è¿è¡çæ¬ç®¡ç</a>ä¸æéç½®**å¤è¿ç¨ä»åº**ï¼`ENABLE_GITLAB` å°±åºè¯¥å¡« `gitee`ã  

### Windows
```powershell
$ .\gh\ci.ps1 <COMMAND> [COMMIT MESSAGE]
```

* `<COMMAND>`ï¼ é»è®¤ä¸º `save` æè `dist`ï¼å¯ä»¥å¨éç½®æä»¶ä¸­èªè¡è®¾ç½®  
* `[COMMIT MESSAGE]`ï¼ ä¼ éå°å®é `commit` å½ä»¤ç commit message  

#### å¸¸è§
æ·»å å·¥ä½åºçææåå¨æä»¶å°æ¬å°ä»åºï¼  
```powershell
$ .\gh\ci.ps1
```

#### ä¿å­
æäº¤å½ååæ¯çææåå¨ï¼å¹¶ push å°è¿ç¨ä»åºï¼  
```powershell
$ .\gh\ci.ps1 save
```

> é»è®¤ç commit message æ¯ `Updated @yyyy-MM-dd HHï¼mmï¼ss` è¿æ ·çæ ¼å¼ã  

---

å¯ä»¥ä½¿ç¨é¿ commit messageï¼æ¨èç¨åå¼å·åè£¹èµ·æ¥ï¼ä»¥åäº§çæ­§ä¹ï¼  
```powershell
$ .\gh\ci.ps1 save "fixï¼ It's a very long commit message & Closes #123, #456"
```

---

å¯ä»¥çç¥å¼å·ï¼åªæç¬¬ä¸ä¸ªåæ°ä¼è¢«è¯å«ä¸ºå½ä»¤ï¼å©ä½çåæ°ä¼èªå¨å½ç±»ä¸ºä¸æ¡ commit messageã  
ä½è¦æ³¨æä¸è½æå½±å PowerShell åè½çç¹æ®ç¬¦å·ï¼æ¯å¦ `&` / `|`/ `#` ç­ï¼ï¼  
```powershell
$ .\gh\ci.ps1 save commit message without special syntax
```

---

å¯ä»¥ä½¿ç¨ç¼©åçå½ä»¤ï¼  
```powershell
$ .\gh\ci.ps1 sa
```

---

ç¼©åçå½ä»¤ä¹æ¯å¯ä»¥æ·»å  commit message çï¼  
```powershell
$ .\gh\ci.ps1 s init
```

#### åå
ä¿æå¤äº `å½ååæ¯` çæåµä¸ï¼å° `å½ååæ¯` åå¹¶å° `ä¸»åæ¯`ï¼å¹¶æäº¤ `ä¸»åæ¯`ï¼  

```powershell
$ .\gh\ci.ps1 dist
$ .\gh\ci.ps1 d # æ³¨ædä¸å¨å³é®è¯saveé å¦åä¼ä¼åè§¦åsave
```

### Linux
```bash
$ chmod +x ./gh/ci
$ ./gh/ci
```

## æ´æ°
```bash
$ git submodule update --rebase --remote
```

èæ¬ä¹æèªæ´æ°åè½ï¼Windows è¿è¡ï¼  
```bash
$ .\gh\ci.ps1 update
```

Linux è¿è¡ï¼  
```bash
$ ./gh/ci update
```
