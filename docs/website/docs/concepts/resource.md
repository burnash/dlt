---
sidebar_position: 1
---

# Resource

A [resource](../glossary.md#resource) is a data producing method. To create a resource, we add the `@resource` decorator to a generator function

arguments:
- `name` The name of the table generated by this resource. Defaults to resource name.
- `write_disposition` How should the data be loaded at destination? Currently supported: `append`, `replace`. Defaults to `append.`
- `depends_on` You can make a resource depend on another, for example for the use case when you need to pass data from a resource to another, or for cases where you want to request field renames before the fields.

Example:

```python
@resource(name='table_name', write_disposition='replace')
def generate_rows(nr):
	for i in range(nr):
		yield {'id':i, 'example_string':'abc'}
```

To get the data of a resource, we could do

```python

for row in games():
		print row

for row in sql_source().resources.get('table_users')
		print(row)

```