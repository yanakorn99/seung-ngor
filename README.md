# seung-<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <title>แอพเซิงงัว</title>
  <style>
    body { font-family: 'Tahoma', sans-serif; padding: 20px; max-width: 700px; margin: auto; }
    label { display: block; margin-top: 10px; }
    input, textarea { width: 100%; padding: 8px; margin-top: 5px; }
    .output { margin-top: 15px; background: #f4f4f4; padding: 10px; }
    button { margin-top: 20px; padding: 10px 20px; }
  </style>
</head>
<body>
  <h2>แอพเซิงงัว</h2>

  <label>อัพโหลดรูปแม่พันธุ์วัว</label>
  <input type="file">

  <label>ชื่อแม่พันธุ์วัว</label>
  <input type="text" id="motherName">

  <label>วัน/เดือน/ปี เกิด (แม่พันธุ์)</label>
  <input type="date" id="motherBirth">

  <label>ชื่อพ่อของแม่พันธุ์</label>
  <input type="text">

  <label>ชื่อแม่ของแม่พันธุ์</label>
  <input type="text">

  <hr>

  <label>ชื่อพ่อพันธุ์วัว</label>
  <input type="text" id="fatherName">

  <label>วัน/เดือน/ปี เกิด (พ่อพันธุ์)</label>
  <input type="date">

  <label>ชื่อพ่อของพ่อพันธุ์</label>
  <input type="text">

  <label>ชื่อแม่ของพ่อพันธุ์</label>
  <input type="text">

  <label>อัพโหลดรูปพ่อพันธุ์</label>
  <input type="file">

  <hr>

  <label>วันที่ผสมพันธุ์</label>
  <input type="date" id="matingDate">

  <div class="output">
    <p>**วันคลอดโดยประมาณ:** <span id="calvingDate">-</span></p>
    <p>กลับสัดครั้งที่ 1 (21 วัน): <span id="heat1">-</span></p>
    <p>กลับสัดครั้งที่ 2 (42 วัน): <span id="heat2">-</span></p>
    <p>กลับสัดครั้งที่ 3 (66 วัน): <span id="heat3">-</span></p>
  </div>

  <label>รายละเอียดเพิ่มเติม</label>
  <textarea></textarea>

  <button onclick="saveData()">บันทึกข้อมูล</button>

  <script>
    const matingInput = document.getElementById('matingDate');
    const calvingDate = document.getElementById('calvingDate');
    const heat1 = document.getElementById('heat1');
    const heat2 = document.getElementById('heat2');
    const heat3 = document.getElementById('heat3');

    matingInput.addEventListener('change', () => {
      const date = new Date(matingInput.value);
      if (isNaN(date)) return;

      const format = d => d.toLocaleDateString('th-TH');

      const addDays = (d, days) => new Date(d.getTime() + days * 86400000);
      const addMonths = (d, months) => {
        const newDate = new Date(d);
        newDate.setMonth(newDate.getMonth() + months);
        return newDate;
      };

      calvingDate.textContent = format(addMonths(date, 9));
      heat1.textContent = format(addDays(date, 21));
      heat2.textContent = format(addDays(date, 42));
      heat3.textContent = format(addDays(date, 66));
    });

    function saveData() {
      alert("ข้อมูลถูกบันทึกเรียบร้อยแล้ว (จำไว้ในเบราว์เซอร์)");
    }
  </script>
</body>
</html>
