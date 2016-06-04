感谢感谢老师做了这个爬虫闯关系列(http://www.heibanke.com/lesson/crawler_ex04)，让大家学习到不少知识。
分享我闯关成功的过程:
ps:第1~3关就不说了，大家看老师的讲解吧。

 第四关：从密码的位置(随机)和密码的值中找出密码。

    解题过程：
        第一次:    我发现password列表共13页，所以我以为只要将列表中不重复的位置的值加到一个list中。再将list转换为一个int的密码，就是登录密码。在尝试多次登录失败后，我发现13页的密码长度不超过70位。这时，我没想到密码会是100位的。。。

        第二次:    在讨论区看到有人成功了，于是去学习经验，看到密码长度是100位，就想到怎么过关了。只要将第一次闯关的代码改动一下，加入密码长度判断，到达100位时就尝试登录。
        
  第五关：识别验证码

     解题过程：

            1、    在这一关中，所需要的登录信息如下(用firebug抓取到的)：
                    1:username，2:csrfmiddlewaretoken,    3:password,    4:captcha_0,     5:captcha_1

            1.1    1、2两项我们都知道。password:老师并没给出密码提示，只能按照第2、3关密码0~30尝试。captcha_0:是登录页面上一个隐藏的值(可以获取到)，对应的应该是验证码在服务器的值。captcha_1：验证码。
            
            1.2    验证码识别是参考python网络数据采集这本书中11.3节：读取验证码与训练Tesseract。经测试，Tesseract识别率在16%左右(因为我没有训练样本)，我们可以通过对识别出的验证码加以验证就知道是否可以用来登录，因为验证码是有规律的;长度为4，全是大写字母，这样登录的话有50%几率验证码正确。
                    --Tesseract：Tesseract是一个OCR库，参考：https://github.com/tesseract-ocr/tesseract/wiki
