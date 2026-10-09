JRUNG WEBSITE V62 + FIREBASE CLOUD SYNC

Cai moi trong ban nay:
- Lam lai giao dien muc Bo nho website va hai nut Sao luu / Khoi phuc theo phong cach toi, gon va de bam tren dien thoai.
- Them ghi chu ro rang ve viec du lieu hien dang nam trong bo nho cua trinh duyet.
- Giu nguyen co che sao luu JSON va khoi phuc thu vien hien co.

QUAN TRONG - DONG BO GIUA CAC APP / THIET BI
Website tinh tren GitHub Pages khong tu dong dong bo IndexedDB/localStorage giua Chrome, app khac, hoac dien thoai khac. Ban sao luu JSON chi chuyen du lieu thu cong. De anh/video tu dong hien o moi noi, can cau hinh dich vu cloud (vi du Firebase hoac Supabase), bao gom project, dang nhap va quyen truy cap. Khong nen nhung mat khau quan tri hay secret key vao HTML cong khai.

Cach cap nhat:
1. Giai nen ZIP.
2. Tai len index.html va hai file video Reze_Hoa.mp4, Reze_Yen_Binh.mp4 len cung thu muc goc tren GitHub Pages (giu dung ten file).
3. Mo website va tai lai trang.


FIREBASE SYNC (V63)
1. Firebase Console: tao project va Add app > Web. Copy firebaseConfig vao index.html, tim const firebaseConfig = { ... } va thay cac chuoi PASTE_...
2. Authentication > Sign-in method > bat Email/Password.
3. Storage > Get started. Dung Storage Rules ben duoi (thay vao Rules), sau do Publish:

 rules_version = '2';
 service firebase.storage {
   match /b/{bucket}/o {
     match /users/{uid}/media/{fileName} {
       allow read, write: if request.auth != null && request.auth.uid == uid;
     }
   }
 }

4. GitHub Pages phai duoc phuc vu qua HTTPS. Tai len index.html va 2 video cung thu muc goc.
5. Mo You > Dong bo thu vien, tao tai khoan Email/Password hoac dang nhap cung mot tai khoan tren moi thiet bi, roi bam Dong bo ngay. Moi thiet bi phai bam dong bo de nhan file moi.
6. Luu y: Firebase config web khong phai secret; bao ve du lieu bang Authentication va Rules. File upload duoc luu trong Firebase Storage, co the phat sinh chi phi vuot muc mien phi. Ban nay dong bo them/tai ve media; xoa media o mot thiet bi chua tu dong xoa ban cloud.

Xem FIREBASE_SETUP.txt de cau hinh project, Authentication va Storage Rules.
