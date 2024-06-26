---
title: Dependencies for software compatibility in Gnoppix
---

<section class="heading">
	<div class="container large">
		<h1>Installers</h1>
		<p>These are installers maintained by our community that automate the installation of a Windows program.</p>
		<div class="warning">
			<p>This feature is new and we are still populating the database. Want to <a href="https://docs.gnoppix.com">contribute</a>?</p>
		</div>
		<div class="info">
			<p>We have a new <a href="/appstore">dedicated place</a> for installers.</p>
		</div>
	</div>
</section>

<section class="page">
	<div class="container large">
		<table>
			<thead>
				<tr>
					<th>Name</th>
					<th>Description</th>
					<th>Category</th>
					<th>Actions</th>
				</tr>
			</thead>
			<tbody id="installers">
			</tbody>
		</table>
	</div>
</section>

<script src="https://cdnjs.cloudflare.com/ajax/libs/js-yaml/4.1.0/js-yaml.min.js"></script>
<script>
	var table = document.getElementById("installers");
	document.addEventListener("DOMContentLoaded", function () {
		fetch('https://raw.githubusercontent.com/gnoppix/programs/main/index.yml')
  			.then(response => response.text())
			.then((data) => {
				console.info("Installers database index found.");
				data = jsyaml.load(data)
				for (var item in data) {
					installer = data[item];

					var row = table.insertRow(-1);
					var name = row.insertCell(0);
					var description = row.insertCell(1);
					var category = row.insertCell(2);
					var actions = row.insertCell(3);

					name.innerHTML = `<b>${item}</b>`;
					description.innerHTML = installer["Description"];
					category.innerHTML = `<span class="tag tag-${installer["Category"]}">${installer["Category"]}</span>`;
					actions.innerHTML = `\
						<a href='https://github.com/gnoppix/programs/blob/main/${installer["Category"]}/${item}.yml'>Details</a> | \
						<a href='https://github.com/gnoppix/programs/issues/new/choose'>Report problem</a>`;
				}
			})
			.catch(err => {
				console.error("Failed to fetch Installers database index!");
				throw err
			});
	});
</script>
