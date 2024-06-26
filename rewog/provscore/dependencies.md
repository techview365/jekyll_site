---
title: Dependencies for software compatibility in Gnoppix
---

<section class="heading">
	<div class="container large">
		<h1>Dependencies</h1>
		<p>These packages increase the compatibility of WINE environments with Windows software.</p>
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
			<tbody id="dependencies">
			</tbody>
		</table>
	</div>
</section>

<script src="https://cdnjs.cloudflare.com/ajax/libs/js-yaml/4.1.0/js-yaml.min.js"></script>
<script>
	var table = document.getElementById("dependencies");
	document.addEventListener("DOMContentLoaded", function () {
		fetch('https://raw.githubusercontent.com/gnoppix/dependencies/main/index.yml')
  			.then(response => response.text())
			.then((data) => {
				console.info("Dependencies database index found.");
				data = jsyaml.load(data)
				for (var item in data) {
					dependency = data[item];

					var row = table.insertRow(-1);
					var name = row.insertCell(0);
					var description = row.insertCell(1);
					var category = row.insertCell(2);
					var actions = row.insertCell(3);

					name.innerHTML = `<b>${item}</b>`;
					description.innerHTML = dependency["Description"];
					category.innerHTML = `<span class="tag tag-${dependency["Category"]}">${dependency["Category"]}</span>`;
					actions.innerHTML = `\
						<a href='https://github.com/gnoppix/dependencies/blob/main/${dependency["Category"]}/${item}.yml'>Details</a> | \
						<a href='https://github.com/gnoppix/dependencies/issues/new/choose'>Report problem</a>`;
				}
			})
			.catch(err => {
				console.error("Failed to fetch Dependencies database index!");
				throw err
			});
	});
</script>
