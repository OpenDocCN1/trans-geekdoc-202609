

# 第 11 章：Python 实战项目

在上一章中，我们讨论了设计项目的方法。在本项目中，我们将详细解释一个包含大量背景信息并附带 Python 代码的实战项目的实现过程。请仔细跟随学习。

## 维护与改进

通过 Python 成功实现了控制计算机关机或重启的功能，但这无法满足所有需求。因此，有必要解决这一缺陷：程序不仅能控制本地计算机的关机或重启，还能通过网络远程控制计算机的关机或重启。在发现旧版本缺陷后，开发新版本的过程就是软件的维护与改进。

## 远程控制通道

如果想要远程控制计算机的关机或重启，本地计算机需要联网。联网后，还需要选择一个远程控制通道，例如 Gmail、网页或电子邮件。

## 通过邮件控制 Python 操作计算机 1

只要能与远程通信，就可以作为远程控制的通道。因此，远程控制的通道有很多。在本项目中，选择邮件作为远程控制的通道工具。

## 通过邮件控制 Python 操作计算机 2

本项目使用电子邮件作为远程控制通道，以实现对计算机的远程控制。可以看出，用户向电子邮件发送相应指令，然后指令被传输给 Python 代码（Python 可以定期监控指定指令），最后由 Python 代码控制本地计算机执行相应操作。因此，需要依次开发以下部分：

1.  通过 Python 登录邮箱（当然，也可以选择其他远程控制通道）。
2.  通过 Python 监控并读取指定邮箱的邮件内容。
3.  通过 Python 实现邮件发送功能（非必需）。
4.  核心业务逻辑处理部分。

首先，你需要准备一个邮箱。因为 Gmail 的端口和用法与其他邮箱不同，这里可以使用 Rediff 邮箱进行操作。作者在此准备了一个 Rediff 邮箱（账号或密码可能稍后会被修改，修改后的代码将无法使用，因此大家应注册自己的邮箱）。

- 账号：`example@rediffmail.com`
- 密码：`sample123`

在网页上登录你的邮箱并进行一些设置。默认情况下 SMTP 和 POP3 是关闭的，但通过 Python 代码发送邮件需要 SMTP，通过 Python 代码读取邮件需要 POP3，所以这两项需要先开启。你可以在邮箱个人中心控制面板中选择“设置-客户端 pop/imap/smtp”选项。可以看到，默认 POP3 和 SMTP 均处于关闭状态，因此你需要选择“开启”单选按钮并保存。

开启后，即可使用 Python 代码登录邮箱。可以看到，Rediff 邮箱的默认 POP3 服务器和 SMTP 服务器信息如下。

- POP3 服务器：`pop.rediff.com`
- SMTP 服务器：`smtp.rediff.com`

接下来，我将展示如何使用 Python 代码登录邮箱。登录邮箱的目的不同，所用的模块也不同。

- 如果登录邮箱的目的是发送邮件，可以调用 `smtplib` 下的 `SMTP()` 建立邮件对象，然后调用邮件对象下的 `login()` 方法进行登录。
- 如果登录邮箱的目的是查收邮件，可以调用 `poplib` 下的 `POP3()` 建立邮件对象，然后调用对象下的 `user()` 方法和 `pass_()` 方法设置登录邮箱的账号和密码。设置完成后，即可登录。

接下来，你可以输入以下代码来演示如何登录邮箱。关键部分已添加注释：

```python
# 1. 登录邮箱以发送邮件
import { 输入库 }
# 通过 SMTP () 建立邮件对象，其中的参数为对应邮箱的 SMTP 服务器地址
smpt.call()
```

通过以上练习，大家应该已经掌握了如何使用 Python 代码登录邮箱。需要注意的是，根据使用目的的不同，登录邮箱所用的模块和方法也不同。

接下来，我将展示如何通过 Python 监控并读取指定邮箱的邮件内容。如果想通过 Python 代码读取指定邮箱的邮件信息，需要先通过 POP3 登录对应邮箱，然后调用 `stat()` 获取统计信息。可以通过 `top()` 指定返回邮件信息的前几行并对返回信息进行解码。解码后，可通过 `email.message_from_string()` 将解码信息转换为可识别的邮件信息，再通过 `email.header.decode_header()` 处理可识别的邮件信息，处理后即可读取所需的邮件信息。

例如，如果需要读取最新邮件的标题，可以通过以下代码实现，关键部分已给出详细注释：

```python
print(statistics)
# (此处为数值)
emailmsg = mail.top(statistics[0], 0)
print(emailmsg)
for i in emailmsg[1]:
    newmsg.append(i.decode())
# 查看解码后的信息
title = decode_header(myemailmsg["subject"])
```

通过上述代码，可以直接读取邮件信息。此时，你可以登录网页版邮箱验证是否正确。登录网页版邮箱后，可以看到最新邮件的信息。

可以看到，最新邮件的标题为 "I am a test mail"（我是一封测试邮件），与代码读取输出的结果一致。因此，现在已成功通过代码读取邮箱中的邮件信息。

接下来，介绍如何通过 Python 实现邮件发送功能。这部分程序对本项目并非必需。本项目的目的是通过电子邮件这一远程通道实现对计算机的远程控制，这只需要 Python 监控邮件中的指令信息。发送邮件的环节可以由 Python 代码实现，也可以通过传统邮件实现，所以这部分不是必需的。当然，学习这部分功能并将其编入程序，可以使项目更加完善。

如果需要通过 Python 实现邮件发送功能，可以先通过 SMTP 登录邮箱，然后通过 `email.mime.text` 下的 `MIMEText` 设置要发送邮件的内容，接着调用已登录邮件对象下的 `sendmail()` 实现邮件发送，最后调用邮件对象下的 `close()` 实现连接关闭。

例如，可以使用以下代码发送邮件消息：

```python
mail.login('credentials', 'password')
# (235, B' ok authenticated')
content = MIMEText('I am the specific content of the mail! This email is mainly used to test whether it can be sent.')
content['from'] = 'sample@rediffmail.com'
content['to'] = 'example@rediffmail.com, abcdefg'
```

运行上述代码后，邮件通过 Python 代码发送到指定邮箱。此时，接收方的邮箱将显示刚刚发送的相关邮件信息。

可以看到，接收方的邮箱中已收到相关邮件。如果在收件箱找不到，可以尝试在垃圾箱中查找。为避免进入垃圾箱，可将发件人邮箱地址加入白名单。

现在，相关功能均可通过 Python 代码实现。接下来，我们将整合上述功能，完成整个项目的开发。目前，本项目的核心业务逻辑处理部分已编写完成。主要思路是：首先建立控制本地计算机关机的函数、控制本地计算机重启的函数、读取指定邮箱第一封邮件标题的函数、向指定邮箱发送相应内容的函数等。然后编写一个 `while` 循环，在其中定期登录指定邮箱并读取第一封邮件的标题。如果标题是特定的指定信息，则调用相应的自定义函数执行相应操作，例如标题为 "shutdown"（关机），则可调用关机函数控制本地计算机关机。执行相应操作后，调用邮件发送函数向指定邮箱发送一封新邮件。应避免新邮件的标题与我们定义的指定信息相同。这样，当软件下次监控邮箱中最新邮件的标题时，不会无限地执行之前的操作，因为此时最新邮件的标题已被重置。

本项目的完整代码如下：

```python
def restart():
    import os
    # restart
    os.system('shutdown -r')
    print("restart command executed successfully")

def shutdown():
    import os
    # shutdown
    os.system('shutdown -s')
    print("shutdown command executed successfully")

def read_mail():
    import poplib
    import time
    from email.header import decode_header
    from email.parser import Parser

    mail = poplib.POP3('pop.rediff.com')
    mail.user('weiweitest789@rediff.com')
    mail.pass_('password')  # password omitted for security
    # detect
    # ... logic to get latest mail subject ...
    return subject

def send_mail(subject, body):
    import smtplib
    from email.mime.text import MIMEText
    # ... logic to send mail ...
    pass

# Main loop
while True:
    time.sleep(5)  # every 5s
    # While the program is running, wait for remote instructions.
    subject = read_mail()
    if subject == "Restart":
        restart()
        send_mail("test", "Restart executed")
    elif subject == "Shut Down":
        shutdown()
        send_mail("test", "Shutdown executed")
```

只要在本地计算机上执行上述程序，计算机将始终监听远程指令。例如，家里的计算机正在运行上述程序，但你在办公室。此时，你可以发送一封标题为 "Restart" 的邮件给 `weiweitest789@rediff.com`（即程序中监控的邮箱地址），家里的计算机将自动重启。如果你发送一封标题为 "Shut Down" 的邮件给该邮箱，家里的计算机将自动关机。此时，你可以远程控制计算机重启或关机。

例如，现在远程向程序中监控的邮箱地址（`weiweitest789@rediff.com`）发送一条标题为 "Shut Down" 的消息。程序运行时，等待远程关机指令执行成功。随后计算机自动执行关机操作。重启后，登录接收邮箱查找邮件消息。标题为 "shutdown" 的邮件是刚才手动远程发送的。当本地程序检测到标题为 "shutdown" 时，会自动调用 `send()` 函数发送一封重置邮件，即标题为 "test" 的邮件，然后控制计算机执行关机操作。

至此，该项目已成功编写并实现了其功能。

## 项目实现与总结

至此，该项目已完全实现。在编写这个小项目的过程中，大家了解了项目开发的基本流程并完整地经历了一遍。希望大家在接手软件项目时，能具备项目管理意识。按照标准流程开发项目，将极大地提高大型项目的开发效率。你可以利用这些思路在 Python 中开发你的项目。祝一切顺利！

在下一章中，我们将详细讨论机器学习。让我们开始吧！

