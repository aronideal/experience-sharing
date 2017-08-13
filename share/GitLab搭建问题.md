* 邮件不能收到

        $ sudo gitlab-rails console
        > Notify.test_email('收件人邮箱地址', '邮件标题', '邮件正文').deliver_now

根据提示解决不能收邮件问题。
