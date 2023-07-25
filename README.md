# AUTOMATED EMAIL (PYTHON)
 import smtplib
import ssl
from email.message import EmailMessage

subject = "Email From python"
body = "This is automated email from SATHIYA!"
sender_mail = "ENTER THE SENDER MAIL ID HERE"
reciver_mail = " ENTER THE RECIVER MAIL ID HERE"
password = input("enter a password: ")

message = EmailMessage()
message ["From"] = sender_mail
message ["to"] = reciver_mail
message["subject"] = subject
message.set_content(body)

context = ssl.create_default_context()

print("Sending EMAIL!")
# log in via smtplib because it has flagged this sort of login as "less secure"
# Turn on the less secure opption in -> Gmail-> security-> less secure -> turn "ON"
with smtplib.SMTP_SSL("smtp.gmail.com", 456, context=context) as server:
    server.login(sender_mail,password)
    server.sendmail(sender_mail, reciver_mail, message.as_string())
print ("EMAIL sent successfully")