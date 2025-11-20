<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
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
<th>الاسم</th><th>رقم الجوال</th><th>الخدمة</th><th>التاريخ</th><th>الوقت</th>
</tr>
</thead>
<tbody></tbody>
</table>

<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.2/firebase-app.js";
import { getDatabase, ref, onChildAdded } from "https://www.gstatic.com/firebasejs/9.22.2/firebase-database.js";

const firebaseConfig = {
  apiKey: "AIzaSyA1pDgSGAMKdceGERXgIU9TQ9AN6iTmquM",
  authDomain: "salonbookingdashboard.firebaseapp.com",
  databaseURL: "https://salonbookingdashboard-default-rtdb.firebaseio.com/",
  projectId: "salonbookingdashboard",
  storageBucket: "salonbookingdashboard.appspot.com",
  messagingSenderId: "38824070536",
  appId: "1:38824070536:web:fff486776f347333a73e3d",
  measurementId: "G-DL5C15WYEW"
};

const app = initializeApp(firebaseConfig);
const db = getDatabase(app);

const dashboardRef = ref(db, 'bookings');

onChildAdded(dashboardRef, (snapshot) => {
    const b = snapshot.val();
    const tbody = document.querySelector("#dashboard tbody");
    const tr = document.createElement("tr");
    tr.innerHTML = `
        <td>${b.name}</td>
        <td>${b.phone}</td>
        <td>${b.service}</td>
        <td>${b.date}</td>
        <td>${b.time}</td>
    `;
    tbody.appendChild(tr);
});
</script>
</body>
</html>
