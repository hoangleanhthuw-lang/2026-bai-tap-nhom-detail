<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tiến độ bài tập nhóm — Tài chính Ngân hàng</title>
<style>
  :root{
    --paper:#F7F5F0; --ink:#1E2A32; --ink-soft:#5B6B74; --line:#D8D3C7;
    --navy:#22405A; --brass:#9C7A3C; --done:#4E7A5A; --now:#9C3B3B; --card:#FFFFFF;
  }
  *{box-sizing:border-box;}
  body{margin:0;background:var(--paper);color:var(--ink);font-family:Georgia,"Noto Serif",serif;line-height:1.55;}
  .wrap{max-width:900px;margin:0 auto;padding:56px 24px 90px;}
  .masthead{border-bottom:2px solid var(--ink);padding-bottom:18px;margin-bottom:34px;}
  .masthead .org{font-family:-apple-system,"Segoe UI",sans-serif;font-size:13px;color:var(--ink-soft);margin-bottom:10px;}
  .masthead h1{font-size:26px;font-weight:600;margin:0 0 8px;}
  .masthead .sub{font-family:-apple-system,"Segoe UI",sans-serif;font-size:14px;color:var(--ink-soft);}
  .meta-row{display:flex;flex-wrap:wrap;gap:24px 32px;font-family:-apple-system,"Segoe UI",sans-serif;font-size:13.5px;margin-bottom:40px;}
  .meta-row div span{display:block;color:var(--ink-soft);font-size:12px;margin-bottom:2px;}
  .meta-row div b{font-size:15px;}
  h2{font-size:19px;font-weight:600;margin:52px 0 18px;padding-bottom:8px;border-bottom:1px solid var(--line);}
  .gantt{background:var(--card);border:1px solid var(--line);padding:22px 22px 26px;}
  .gantt-scale{font-family:-apple-system,"Segoe UI",sans-serif;font-size:11px;color:var(--ink-soft);display:flex;justify-content:space-between;margin-bottom:6px;}
  .gantt-track{position:relative;height:34px;background:#EFEBE0;border-radius:2px;overflow:hidden;margin-bottom:16px;}
  .gantt-fill{position:absolute;top:0;left:0;height:100%;background:var(--navy);}
  .gantt-today{position:absolute;top:-4px;bottom:-4px;width:2px;background:var(--now);}
  .gantt-today::after{content:"Hôm nay";position:absolute;top:-20px;left:50%;transform:translateX(-50%);font-family:-apple-system,"Segoe UI",sans-serif;font-size:10.5px;color:var(--now);white-space:nowrap;font-weight:600;}
  .gantt-rows{display:flex;flex-direction:column;gap:10px;}
  .gantt-row{position:relative;height:26px;background:#F2EFE7;border-radius:2px;}
  .gantt-row .bar{position:absolute;top:0;height:100%;border-radius:2px;display:flex;align-items:center;padding:0 8px;font-family:-apple-system,"Segoe UI",sans-serif;font-size:11.5px;color:#fff;white-space:nowrap;overflow:hidden;}
  .bar.done{background:var(--done);}
  .bar.active{background:var(--navy);}
  .bar.upcoming{background:#B9B2A0;color:#4a453a;}
  .legend{display:flex;gap:18px;margin-top:14px;font-family:-apple-system,"Segoe UI",sans-serif;font-size:12px;color:var(--ink-soft);}
  .legend span{display:inline-flex;align-items:center;gap:6px;}
  .dot{width:9px;height:9px;border-radius:2px;display:inline-block;}
  table{width:100%;border-collapse:collapse;font-family:-apple-system,"Segoe UI",sans-serif;font-size:13.5px;}
  th,td{border:1px solid var(--line);padding:10px 12px;text-align:left;vertical-align:top;}
  th{background:#EFEBE0;font-weight:600;font-size:12.5px;color:var(--ink-soft);}
  .status-tag{display:inline-block;padding:2px 8px;border-radius:20px;font-size:11px;font-weight:600;}
  .status-tag.done{background:#E4EEE6;color:var(--done);}
  .status-tag.active{background:#E4EBF1;color:var(--navy);}
  .status-tag.upcoming{background:#EEEEE9;color:var(--ink-soft);}
  .progress-cell{display:flex;align-items:center;gap:8px;}
  .progress-bar{flex:1;height:8px;background:#EFEBE0;border-radius:4px;overflow:hidden;}
  .progress-bar span{display:block;height:100%;background:var(--navy);}
  .progress-pct{font-size:12px;color:var(--ink-soft);min-width:32px;text-align:right;}
  footer{margin-top:60px;padding-top:16px;border-top:1px solid var(--line);font-family:-apple-system,"Segoe UI",sans-serif;font-size:11.5px;color:var(--ink-soft);}
  @media (max-width:600px){.wrap{padding:32px 16px 60px;} .masthead h1{font-size:21px;}}
</style>
</head>
<body>
<div class="wrap">

  <div class="masthead">
    <div class="org">Trường Đại học Ngân hàng TP. Hồ Chí Minh · Chương trình tiếng Anh bán phần</div>
    <h1>Tiến độ bài tập nhóm — Ngành Tài chính – Ngân hàng</h1>
    <div class="sub">Môn IPA · GVHD: PGS.TS Nguyễn Hoàng Chung</div>
  </div>

  <div class="meta-row">
    <div><span>Tên dự án</span><b id="projectName">[Chưa đặt tên]</b></div>
    <div><span>Số thành viên</span><b>5</b></div>
    <div><span>Hình thức</span><b>Tiếng Anh bán phần</b></div>
    <div><span>Giai đoạn hiện tại</span><b id="stageNow">—</b></div>
    <div><span>Hạn chót gần nhất</span><b id="deadlineNext">—</b></div>
  </div>

  <h2>Sơ đồ tiến độ toàn đợt</h2>
  <div class="gantt">
    <div class="gantt-scale"><span id="scaleStart"></span><span id="scaleEnd"></span></div>
    <div class="gantt-track">
      <div class="gantt-fill" id="overallFill"></div>
      <div class="gantt-today" id="overallToday"></div>
    </div>
    <div class="gantt-rows" id="rowsContainer"></div>
    <div class="legend">
      <span><i class="dot" style="background:var(--done)"></i>Đã hoàn thành</span>
      <span><i class="dot" style="background:var(--navy)"></i>Đang diễn ra</span>
      <span><i class="dot" style="background:#B9B2A0"></i>Sắp tới</span>
      <span><i class="dot" style="background:var(--now)"></i>Hôm nay</span>
    </div>
  </div>

  <h2>Chi tiết các mốc</h2>
  <table>
    <thead><tr><th>Stt</th><th>Nội dung</th><th>Thời gian</th><th>Trạng thái</th></tr></thead>
    <tbody id="tableBody"></tbody>
  </table>

  <h2>Các thành viên nhóm & phân công công việc</h2>
  <table>
    <thead><tr><th>Họ tên</th><th>Công việc phân công</th><th>Mức độ hoàn thành</th><th>Ghi chú</th></tr></thead>
    <tbody id="memberBody"></tbody>
  </table>

  <footer>Trang theo dõi nội bộ, cập nhật trạng thái tự động theo ngày truy cập.</footer>
</div>

<script>
// ====== SỬA DỮ LIỆU CỦA NHÓM Ở ĐÂY ======

// Khoảng thời gian toàn đợt (7 tuần)
const overallStart = "2026-09-07";
const overallEnd   = "2026-10-15";

// Các giai đoạn hiển thị trên Gantt — sửa tên và ngày theo kế hoạch thật của nhóm
const stages = [
  { label: "Phân công nhiệm vụ",        start: "2026-09-07", end: "2026-09-13" },
  { label: "Thu thập & nghiên cứu",      start: "2026-09-14", end: "2026-09-27" },
  { label: "Viết nội dung chính",        start: "2026-09-28", end: "2026-10-08" },
  { label: "Chỉnh sửa & hoàn thiện",     start: "2026-10-09", end: "2026-10-13" },
  { label: "Nộp bài",                    start: "2026-10-14", end: "2026-10-15" },
];

// Bảng chi tiết mốc — nên khớp với stages ở trên
const tableRows = [
  { stt: 1, content: "Phân công nhiệm vụ cho từng thành viên", start: "2026-09-07", end: "2026-09-13" },
  { stt: 2, content: "Thu thập tài liệu, nghiên cứu nội dung", start: "2026-09-14", end: "2026-09-27" },
  { stt: 3, content: "Viết nội dung chính của bài", start: "2026-09-28", end: "2026-10-08" },
  { stt: 4, content: "Chỉnh sửa, rà soát, hoàn thiện bài", start: "2026-10-09", end: "2026-10-13" },
  { stt: 5, content: "Nộp bài chính thức", start: "2026-10-14", end: "2026-10-15" },
];

// Danh sách 5 thành viên — thay tên thật, công việc, % hoàn thành, ghi chú
const members = [
  { name: "[Thành viên 1]", task: "[Công việc được giao]", percent: 0, note: "" },
  { name: "[Thành viên 2]", task: "[Công việc được giao]", percent: 0, note: "" },
  { name: "[Thành viên 3]", task: "[Công việc được giao]", percent: 0, note: "" },
  { name: "[Thành viên 4]", task: "[Công việc được giao]", percent: 0, note: "" },
  { name: "[Thành viên 5]", task: "[Công việc được giao]", percent: 0, note: "" },
];

// ====== HẾT PHẦN CẦN SỬA ======

const D = s => new Date(s + "T00:00:00");
const today = new Date(); today.setHours(0,0,0,0);
function pct(d, start, end){ const total = end-start; const pos = Math.min(Math.max(d-start,0),total); return (pos/total)*100; }
function statusOf(start, end){ if (today < start) return "upcoming"; if (today > end) return "done"; return "active"; }

const oStart = D(overallStart), oEnd = D(overallEnd);
document.getElementById("scaleStart").textContent = oStart.toLocaleDateString("vi-VN");
document.getElementById("scaleEnd").textContent = oEnd.toLocaleDateString("vi-VN");
document.getElementById("overallFill").style.width = pct(today, oStart, oEnd) + "%";
document.getElementById("overallToday").style.left = pct(today, oStart, oEnd) + "%";

const rowsContainer = document.getElementById("rowsContainer");
let currentStageLabel = "—";
stages.forEach(s => {
  const start = D(s.start), end = D(s.end);
  const st = statusOf(start, end);
  if (st === "active") currentStageLabel = s.label;
  const left = pct(start, oStart, oEnd), right = pct(end, oStart, oEnd);
  const row = document.createElement("div");
  row.className = "gantt-row";
  row.innerHTML = `<div class="bar ${st}" style="left:${left}%;width:${Math.max(right-left,2)}%">${s.label}</div>`;
  rowsContainer.appendChild(row);
});
document.getElementById("stageNow").textContent = currentStageLabel;

const tbody = document.getElementById("tableBody");
let nextDeadline = null, nextDeadlineLabel = "—";
tableRows.forEach(r => {
  const start = D(r.start), end = D(r.end);
  const st = statusOf(start, end);
  const label = st === "done" ? "Đã hoàn thành" : st === "active" ? "Đang diễn ra" : "Sắp tới";
  if ((st === "upcoming" || st === "active") && (!nextDeadline || end < nextDeadline)) { nextDeadline = end; nextDeadlineLabel = end.toLocaleDateString("vi-VN"); }
  const tr = document.createElement("tr");
  tr.innerHTML = `<td>${r.stt}</td><td>${r.content}</td><td>${start.toLocaleDateString("vi-VN")} – ${end.toLocaleDateString("vi-VN")}</td><td><span class="status-tag ${st}">${label}</span></td>`;
  tbody.appendChild(tr);
});
document.getElementById("deadlineNext").textContent = nextDeadlineLabel;

const memberBody = document.getElementById("memberBody");
members.forEach(m => {
  const tr = document.createElement("tr");
  tr.innerHTML = `<td>${m.name}</td><td>${m.task}</td>
    <td><div class="progress-cell"><div class="progress-bar"><span style="width:${m.percent}%"></span></div><span class="progress-pct">${m.percent}%</span></div></td>
    <td>${m.note}</td>`;
  memberBody.appendChild(tr);
});
</script>
</body>
</html>
