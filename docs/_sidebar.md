<!-- docs/_sidebar.md -->
- [Home](./readme.md)
- [Architecture Overview](./arch_overview.md)
- [Why Use AuTest?](./Why_AuTest.md)
- </head>
<body>
  <ul>
    <li><a href="./sample2.md">Tests</a>
      <details>
        <summary><strong>MOCA</strong></summary>
        <ul>
          <li><a href="#" onclick="showLinks('moca-links')">BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001</a></li>
          <li><a href="./tests_docs/BASE_INB_0002100_TRLR_CKIN_MOCA_V001.md">BASE_INB_0002100_TRLR_CKIN_MOCA_V001</a></li>
          <li><a href="./tests_docs/BASE_INB_0003100_IDENTIFY_MOCA_V001.md">BASE_INB_0003100_IDENTIFY_MOCA_V001</a></li>
          <!-- Add other MOCA links here -->
        </ul>
      </details>
    </li>
  </ul>

  <div id="moca-links" class="hidden">
    <h2>MOCA</h2>
    <ul>
      <li><a href="./tests_docs/BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001.md">BASE_INB_0001100_COPY_TEMPLATE_RCVTRK_MOCA_V001</a></li>
      <li><a href="./tests_docs/BASE_INB_0002100_TRLR_CKIN_MOCA_V001.md">BASE_INB_0002100_TRLR_CKIN_MOCA_V001</a></li>
      <li><a href="./tests_docs/BASE_INB_0003100_IDENTIFY_MOCA_V001.md">BASE_INB_0003100_IDENTIFY_MOCA_V001</a></li>
      <!-- Add other MOCA links here -->
    </ul>
  </div>

  <script>
    function showLinks(id) {
      const element = document.getElementById(id);
      if (element.classList.contains('hidden')) {
        element.classList.remove('hidden');
        element.classList.add('visible');
      } else {
        element.classList.remove('visible');
        element.classList.add('hidden');
      }
    }
  </script>
</body>
</html>

