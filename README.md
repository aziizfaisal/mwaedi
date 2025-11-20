<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>Dashboard الحجوزات</title>
<style>
body { font-family: Arial; background:#111; color:#fff; margin:0; padding:20px; }
h1 { text-align:center; color:#d4a056; }
table { width:100%; border-collapse: collapse; margin-top:20px; }
th, td { border:1px solid #333; padding:12px; text-align:center; }
th { background:#222; }
tr:nth-child(even){ background:#1a1a1a; }
</style>
</head>
<body>
<h1>Dashboard الحجوزات</h1>
<table id="dashboard">
<thead>
<tr>
<th>الاسم</th>
<th>رقم الجوال</th>
<th>الخدمة</th>
<th>التاريخ</th>
<th>الوقت</th>
</tr>
</thead>
<tbody></tbody>
</table>

<script src="https://www.gstatic.com/firebasejs/9.22.2/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.22.2/firebase-database-compat.js"></script>
<script>
// Firebase Config نفسه
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT.firebaseio.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
firebase.initializeApp(firebaseConfig);
const db = firebase.database();

const tbody = document.querySelector("#dashboard tbody");

// تحديث لحظي
db.ref("bookings").on("child_added", snapshot => {
    const booking = snapshot.val();
    const tr = document.createElement("tr");
    tr.innerHTML = `<td>${booking.name}</td><td>${booking.phone}</td><td>${booking.service}</td><td>${booking.date}</td><td>${booking.time}</td>`;
    tbody.appendChild(tr);
});
</script>
</body>
</html>
