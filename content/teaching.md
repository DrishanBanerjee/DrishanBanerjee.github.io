---
title: "Teaching"
date: 2026-09-01
hidemeta: true
description: "Teaching experience of Drishan Banerjee at UC Santa Cruz."

---

---

##### Instructor of Record at UCSC <span class="eval-col">Selected student evaluations</span>

+ ECON 294A(R) – Applied Economics and Finance Laboratory (Graduate), 2026 <button class="eval-btn" data-course="econ294ar">View</button>
+ ECON 2 – Introductory Macroeconomics (Undergraduate), 2025, 2026 <button class="eval-btn" data-course="econ2ior">View</button>

---

##### Teaching Assistant at UCSC <span class="eval-col">Selected student evaluations</span>

+ ECON 233 – Finance (Graduate), 2025 <a class="course-btn" href="/teaching/econ233/">Course materials</a> <button class="eval-btn" data-course="econ233">View</button>
+ ECON 100A – Intermediate Microeconomics (Undergraduate), 2025 <button class="eval-btn" data-course="econ100a">View</button>
+ ECON 2 – Introductory Macroeconomics (Undergraduate), 2024, 2026 <button class="eval-btn" data-course="econ2">View</button>
+ ECON 113 – Introductory Econometrics (Undergraduate), 2023, 2024 <button class="eval-btn" data-course="econ113">View</button>
+ ECON 126 – Why Economies Succeed or Fail (Undergraduate), 2022 <button class="eval-btn" data-course="econ126">View</button>
+ ECON 101 – Managerial Economics (Undergraduate), 2024 <button class="eval-btn" data-course="econ101">View</button>
+ COWL 52 – Personal Finance (Undergraduate), 2023
+ ECON 197 – Economic Rhetoric (Undergraduate), 2023

---

##### Teaching Evaluations

Full evaluations available upon request.

<dialog id="eval-dialog" aria-labelledby="eval-title">
  <div class="eval-head">
    <div>
      <div id="eval-title" class="eval-title"></div>
      <div class="eval-sub">Selected student evaluations</div>
    </div>
    <button class="eval-close" aria-label="Close">&times;</button>
  </div>
  <div class="eval-tabs" role="tablist"></div>
  <div class="eval-body"></div>
</dialog>

<script>
(function () {
  var base = "/teaching/evals/";

  // g("econ113-fall2023", 5) -> the 5 graph files for that quarter
  function g(slug, n) {
    var out = [];
    for (var i = 1; i <= n; i++) out.push("graphs/" + slug + "-" + (i < 10 ? "0" : "") + i + ".png");
    return out;
  }

  // Each quarter: [label, comment screenshots, graph groups [[group label, files], ...]]
  var evals = {
    econ294ar: { title: "ECON 294A(R) – Applied Economics and Finance Laboratory",
      quarters: [["Winter 2026", ["econ294ar-winter2026.png"],
                  [["Section 1", g("econ294ar-winter2026-s1", 10)],
                   ["Section 2", g("econ294ar-winter2026-s2", 9)]]]] },
    econ2ior: { title: "ECON 2 – Introductory Macroeconomics",
      quarters: [["Summer 2025", [], [["", g("econ2-summer2025", 6)]]]] },
    econ233: { title: "ECON 233 – Finance",
      quarters: [["Fall 2025", ["econ233-fall2025.jpg"], [["", g("econ233-fall2025", 5)]]]] },
    econ100a: { title: "ECON 100A – Intermediate Microeconomics",
      quarters: [["Summer 2025", ["econ100a-summer2025.png"], [["", g("econ100a-summer2025", 5)]]]] },
    econ2: { title: "ECON 2 – Introductory Macroeconomics",
      quarters: [["Winter 2024", ["econ2-winter2024.png"], [["", g("econ2-winter2024", 3)]]],
                 ["Spring 2026", ["econ2-spring2026.png"], [["", g("econ2-spring2026", 5)]]]] },
    econ113: { title: "ECON 113 – Introductory Econometrics",
      quarters: [["Fall 2023", ["econ113-fall2023-1.png", "econ113-fall2023-2.png"], [["", g("econ113-fall2023", 5)]]],
                 ["Spring 2024", ["econ113-spring2024.png"], [["", g("econ113-spring2024", 6)]]],
                 ["Fall 2024", ["econ113-fall2024-1.png", "econ113-fall2024-2.png"], [["", g("econ113-fall2024", 5)]]]] },
    econ126: { title: "ECON 126 – Why Economies Succeed or Fail",
      quarters: [["Fall 2022", ["econ126-fall2022.png"], [["", g("econ126-fall2022", 5)]]]] },
    econ101: { title: "ECON 101 – Managerial Economics",
      quarters: [["Summer 2024", [], [["", g("econ101-summer2024", 6)]]]] }
  };

  var dlg = document.getElementById("eval-dialog");
  var tabs = dlg.querySelector(".eval-tabs");
  var body = dlg.querySelector(".eval-body");

  function show(course, idx) {
    var c = evals[course];
    tabs.querySelectorAll("button").forEach(function (b, i) {
      b.setAttribute("aria-selected", i === idx ? "true" : "false");
    });
    var q = c.quarters[idx];
    body.innerHTML = "";
    function heading(text, cls) {
      var h = document.createElement("div");
      h.className = cls;
      h.textContent = text;
      body.appendChild(h);
    }
    function addImg(f) {
      var img = document.createElement("img");
      img.src = base + f;
      img.alt = c.title + ", " + q[0];
      img.loading = "lazy";
      body.appendChild(img);
    }
    if (q[1].length) {
      heading("Student comments", "eval-section");
      q[1].forEach(addImg);
    }
    if (q[2].length) {
      heading("Student ratings", "eval-section");
      q[2].forEach(function (grp) {
        if (grp[0]) heading(grp[0], "eval-group");
        grp[1].forEach(addImg);
      });
    }
    body.scrollTop = 0;
  }

  function open(course) {
    var c = evals[course];
    dlg.querySelector(".eval-title").textContent = c.title;
    tabs.innerHTML = "";
    c.quarters.forEach(function (q, i) {
      var b = document.createElement("button");
      b.setAttribute("role", "tab");
      b.textContent = q[0];
      b.addEventListener("click", function () { show(course, i); });
      tabs.appendChild(b);
    });
    tabs.style.display = c.quarters.length > 1 ? "" : "none";
    show(course, c.quarters.length - 1);
    dlg.showModal();
    body.scrollTop = 0;
    requestAnimationFrame(function () { body.scrollTop = 0; });
  }

  document.querySelectorAll(".eval-btn").forEach(function (b) {
    b.addEventListener("click", function () { open(b.dataset.course); });
  });
  dlg.querySelector(".eval-close").addEventListener("click", function () { dlg.close(); });
  dlg.addEventListener("click", function (e) { if (e.target === dlg) dlg.close(); });
})();
</script>
