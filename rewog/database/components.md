---
title: Gnoppix components
---

<section class="heading">
	<div class="container large">
		<h1>Components</h1>
		<p>These are essential elements for creating environments and extending them with new features and implementations.</p>
	</div>
</section>

<section class="page">
	<div class="container large">
		<table>
			<thead>
				<tr>
					<th>Name</th>
					<th>Category</th>
					<th>Type</th>
					<th>Channel</th>
					<th>Actions</th>
				</tr>
			</thead>
			<tbody id="components">
			</tbody>
		</table>
	</div>
</section>

<script src="https://cdnjs.cloudflare.com/ajax/libs/js-yaml/4.1.0/js-yaml.min.js"></script>
<script>
	var table = document.getElementById("components");
	document.addEventListener("DOMContentLoaded", function () {
		fetch('https://raw.githubusercontent.com/gnoppix/components/main/index.yml')
  			.then(response => response.text())
			.then((data) => {
				console.info("Components database index found.");
				data = jsyaml.load(data)
				for (var item in data) {
					component = data[item];

					var row = table.insertRow(-1);
					var name = row.insertCell(0);
					var category = row.insertCell(1);
					var type = row.insertCell(2);
					var channel = row.insertCell(3);
					var actions = row.insertCell(4);

                    sub_category = component["Sub-category"] ? component["Sub-category"] : "n/a";
                    sub_category_url = component["Sub-category"] ? `/${component["Sub-category"]}` : "";

					name.innerHTML = `<b>${item}</b>`;
					type.innerHTML = sub_category
					channel.innerHTML = component["Channel"];
					category.innerHTML = `<span class="tag tag-${component["Category"]}">${component["Category"]}</span>`;
					actions.innerHTML = `\
						<a href='https://github.com/gnoppix/components/blob/main/${component["Category"]}${sub_category_url}/${item}.yml'>Details</a> | \
						<a href='https://github.com/gnoppix/components/issues/new/choose'>Report problem</a>`;
				}
			})
			.catch(err => {
				console.error("Failed to fetch Components database index!");
				throw err
			});
	});
</script>
