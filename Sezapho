import itertools
import string
import requests
import time

# توليد الأحرف والأرقام الممكنة
characters = string.ascii_lowercase + string.digits

# توليد كل التركيبات الرباعية
combinations = [''.join(p) for p in itertools.product(characters, repeat=4)]

# الدالة للتحقق من توافر اسم المستخدم على إنستجرام
def check_availability(username):
    url = f"https://www.instagram.com/{username}/"
    try:
        response = requests.get(url)
        if response.status_code == 404:
            return True  # المستخدم غير موجود
        elif response.status_code == 200:
            return False  # المستخدم موجود
    except Exception as e:
        print(f"Error checking {username}: {e}")
    return False

# فتح الملف لكتابة الأسماء المتاحة
with open('available_usernames.txt', 'w') as file:
    # التحقق من التركيبات المتاحة
    for username in combinations:
        if check_availability(username):
            print(f"Username {username} is available")
            file.write(username + '\n')
        # تأخير بسيط لتجنب الحظر من قبل السيرفر
        time.sleep(1)  # يمكن تعديل التأخير حسب الحاجة

print("Finished checking usernames.")
