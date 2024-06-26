---
title: AppStore
---

<section class="heading">
  <div class="container large center">
    <h1>AppStore</h1>
    <p>Running Windows application under Linux redefined</p>
    <input class="store-search" type="search" autocomplete="off" placeholder="Epic Games Store" />
  </div>
</section>

<section class="page">
  <div class="container large">
    <div class="warning">
			<p>The 1-click and run feature is a core Gnoppix PRO feature that makes it easy to run Windows applications on Linux. It has just been released with Gnoppix PRO and we are just starting to populate this list. Do you want to <a href="https://discord.com/invite/tmHjQmgBW9">contribute</a>?</p>
    </div>
    <br />
    <div class="filters">
      <span class="tag grade-all active" grade="All">All</span>
      <span class="tag grade-Platinum" grade="Platinum">Platinum</span>
      <span class="tag grade-Gold" grade="Gold">Gold</span>
      <span class="tag grade-Silver" grade="Silver">Silver</span>
      <span class="tag grade-Bronze" grade="Bronze">Bronze</span>
    </div>
    <br />
    <div class="store store-results">
    </div>
  </div>
</section>

<div class="modal" id="modal_installer"></div>
<div class="modal" id="modal_review"></div>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.2.0/styles/obsidian.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.2.0/highlight.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.2.0/languages/yaml.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/js-yaml/4.1.0/js-yaml.min.js"></script>
<script src="/assets/js/store-common.js"></script>
<script>
  document.querySelector('.store-search').addEventListener('keyup', function(e) {
    var search = this.value.toLowerCase();
    var cards = document.querySelectorAll('.store .card');
    for (var i = 0; i < cards.length; i++) {
      var card = cards[i];
      var text = card.innerText.toLowerCase();
      if (text.indexOf(search) > -1) {
        card.style.display = 'block';
      } else {
        card.style.display = 'none';
      }
    }
  });
  document.querySelectorAll('.filters .tag').forEach(function(tag) {
    tag.addEventListener('click', function(e) {
      var grade = this.getAttribute('grade');
      document.querySelectorAll('.filters .tag').forEach(function(tag) {
        tag.classList.remove('active');
      });
      this.classList.add('active');
      document.querySelectorAll('.store .card').forEach(function(card) {
        if (grade == 'All') {
          card.style.display = 'block';
        } else {
          if (card.getAttribute('grade') == grade) {
            card.style.display = 'block';
          } else {
            card.style.display = 'none';
          }
        }
      });
    });
  });
  var store = document.getElementsByClassName("store");
  document.addEventListener("DOMContentLoaded", function () {
    fetch('https://raw.githubusercontent.com/gnoppix/programs/main/index.yml')
      .then(response => response.text())
      .then((data) => {
        console.info("Installers database index found.");
        data = jsyaml.load(data)
        for (var item in data) {
          installer = data[item];
          icon = `https://github.com/gnoppix/programs/blob/main/data/${item}/${installer["Icon"]}?raw=true`;
          var card = `<div class="card" grade="${installer["Grade"]}">
            <div class="card-content">
              <div class="card-bg" style="background-image: url(${icon})"></div>
              <h3>
                <a href="/app#${item}">
                  <img src="${icon}" alt="${item}" />
                  ${installer["Name"]}
                </a>
              </h3>
              <div class="dropdown">
                <div class="toggler">
                  <ion-icon class="icon" name="chevron-down-outline"></ion-icon>
                </div>
                <ul>
                  <li>
                    <a href='https://github.com/gnoppix/gnoppix/issues/new/choose' tooltip='Bug report'>
                      <ion-icon class="icon" name="bug-outline"></ion-icon> <span>Bug report</span>
                    </a>
                  </li>
                  <li>
                    <a onclick='modal("https://raw.githubusercontent.com/gnoppix/programs/main/${installer["Category"]}/${item}.yml")' tooltip='Show installer'>
                      <ion-icon class="icon" name="code-outline"></ion-icon> <span>Show installer</span>
                    </a>
                  </li>
                </ul>
              </div>
              <p>${installer["Description"]}</p>
              <div class="tags">
                <span class="tag grade-${installer["Grade"]}">${installer["Grade"]}</span>
                <span class="tag tag-${installer["Category"]}">${installer["Category"]}</span>
              </div>
              <div class="actions">
                <a href='https://docs.gnoppix.com/installers#use-installers' tooltip='How to install'> <!--gnoppix:${item}-->
                  <ion-icon class="icon" name="download-outline"></ion-icon> Install
                </a>
              </div>
            </div>
          </div>`;
          store[0].innerHTML += card;
        }
      })
      .catch(err => {
        console.error("Failed to fetch Installers database index!");
        throw err
      });
  });
</script>
