# coursechemist-
makes course from web browser 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Course Maker</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f9f9f9; margin: 0; }
    header { background: #4CAF50; color: white; padding: 1em; text-align: center; }
    #menu { background: #eee; padding: 1em; width: 200px; float: left; height: 100vh; box-sizing: border-box; }
    #content { margin-left: 220px; padding: 2em; }
    button { display: block; margin: 0.5em 0; width: 100%; }
    textarea { width: 100%; height: 150px; }
  </style>
</head>
<body>

<header>
  <h1>Simple Course Maker</h1>
</header>

<div id="menu">
  <button onclick="addLesson()">Add Lesson</button>
  <div id="lessonList"></div>
</div>

<div id="content">
  <h2 id="lessonTitle">Welcome</h2>
  <textarea id="lessonContent" placeholder="Write lesson content here..."></textarea>
</div>

<script>
  let lessons = [];

  function addLesson() {
    const title = prompt("Enter lesson title:");
    if (title) {
      const lesson = { title, content: "" };
      lessons.push(lesson);
      renderLessonList();
    }
  }

  function renderLessonList() {
    const listDiv = document.getElementById('lessonList');
    listDiv.innerHTML = '';
    lessons.forEach((lesson, index) => {
      const btn = document.createElement('button');
      btn.textContent = lesson.title;
      btn.onclick = () => showLesson(index);
      listDiv.appendChild(btn);
    });
  }

  function showLesson(index) {
    const lesson = lessons[index];
    document.getElementById('lessonTitle').textContent = lesson.title;
    const contentArea = document.getElementById('lessonContent');
    contentArea.value = lesson.content;
    contentArea.oninput = () => lesson.content = contentArea.value;
  }
</script>

</body>
</html>
