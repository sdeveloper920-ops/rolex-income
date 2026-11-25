ROLEX INCOME — NETLIFY + FIREBASE MVP

এই ZIP-এ আছে:
- 𝐑𝐎𝐋𝐄𝐗 𝐈𝐍𝐂𝐎𝐌𝐄 ব্র্যান্ডিং ও ডাবল-রিং লোগো
- Firebase Google sign-in
- Member dashboard ও server-side balance
- দৈনিক task claim (প্রতি user/task/day একবার)
- Manual bKash/Nagad/Rocket deposit request
- Withdraw request; pending অবস্থায় balance reserve হয়
- Admin task create/enable/disable ও payment request approve/reject
- Firestore client rules deny-by-default
- Netlify Function API

গুরুত্বপূর্ণ সীমাবদ্ধতা:
- এটি পরীক্ষামূলক MVP; বাস্তব আর্থিক সেবা হিসেবে এখনো production-ready নয়।
- Referral bonus payout, automated payment gateway, KYC, fraud monitoring,
  full audit/export, customer support এবং legal/compliance workflow নেই।
- Admin approve করার আগে payment transaction নিজে যাচাই করতে হবে।
- কোনো আয়ের নিশ্চয়তা নেই।

প্রয়োজনীয় সেটআপ (একবার):
1) Firebase Console-এ Authentication > Sign-in method > Google Enable করুন।
2) Authentication > Settings > Authorized domains-এ আপনার Netlify domain যোগ করুন।
3) Firestore Database তৈরি করুন এবং এই ZIP-এর firestore.rules publish করুন।
4) Firebase Project settings > Service accounts থেকে service account JSON key তৈরি করুন।
   এই key কখনো public করবেন না, কাউকে পাঠাবেন না, ZIP/GitHub-এ রাখবেন না।
5) Netlify Dashboard > Site configuration > Environment variables-এ যোগ করুন:
   Key: FIREBASE_SERVICE_ACCOUNT
   Value: Firebase service-account JSON-এর সম্পূর্ণ contents।
6) ZIP-টি GitHub repository-তে upload করে Netlify-তে Add new site > Import from Git
   দিয়ে deploy করুন। Netlify Functions চালাতে Git-connected deploy ব্যবহার করুন;
   শুধু manual drag-and-drop static deploy-এ Functions চলবে না।
7) Netlify deploy-এর পর Google login এবং test account দিয়ে সব flow পরীক্ষা করুন।
8) Netlify ও Firebase billing/usage limits পরীক্ষা করুন। Free tier সীমা অতিক্রম করলে
   খরচ হতে পারে।

Admin email:
sdeveloper920@gmail.com

নিরাপত্তা:
- FIREBASE_SERVICE_ACCOUNT কেবল Netlify Environment Variables-এ থাকবে।
- Firebase web config browser-এ থাকা স্বাভাবিক; service-account private key কখনো নয়।
- Firestore client access বন্ধ; সব পরিবর্তন verified Netlify server function দিয়ে হয়।
- Netlify environment variable পরিবর্তনের পর নতুন deploy করুন।

বর্তমান UI/Backend MVP-তে admin email নির্দিষ্ট করা আছে।
Production-এ ব্যবহারের আগে independent security review ও end-to-end test করান।
