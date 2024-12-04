# 2025 Hyland Hackathon
[January 11-12](ImportantTimes.md) | [Hyland HQ](GettingToHyland.md)

Your journey begins here. To prepare for your experience, here are some important items to complete:

<ul style="list-style-type: none">
  <input type="checkbox" id="item1" checked> Visit this website<br>
  <input type="checkbox" id="item2"> Make sure you have a <a href="AdmissionForms.md">consent form</a> on file<br>
  <input type="checkbox" id="item3"> Join the <a href="https://discord.gg/pufaaWJaAH">Discord Server</a><br>
  <input type="checkbox" id="item4"> Choose a <a href="Tracks.md">Track</a> to follow<br>
  <input type="checkbox" id="item5"> Form a <a href="TeamFormation.md">Team</a><br>
  <input type="checkbox" id="item6"> Gather your <a href="WhatToBring.md">Supplies</a><br>
  <input type="checkbox" id="item7"> Familiarize yourself with the <a href="ImportantTimes.md">Important Times</a><br>
  <input type="checkbox" id="item8"> Chart your course to <a href="GettingToHyland.md">Hyland HQ</a><br>
  <input type="checkbox" id="item9"> Reach out to the <a href="Contact.md">Hyland Tech Outreach team</a> if you have any questions<br>
</ul>

<script>
  document.querySelectorAll("input").forEach(inputElement => {
    const elementId = `${inputElement.id}`;

    inputElement.checked = localStorage.getItem(elementId) === 'checked';
    inputElement.onchange = e => {
      if (e.target.checked) {
        localStorage.setItem(elementId, 'checked');
      } else {
          localStorage.setItem(elementId, 'not-checked');
      }
    };
  });
</script>
