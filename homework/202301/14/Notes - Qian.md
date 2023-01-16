# 获取关于参数的信息
`$ curl -i http://localhost:8080/?person=Jim` # Access the endpoint by passing a parameter.

# Positional Class Patterns

The pattern City('Asia') matches any City instance where the first attribute value
is 'Asia', regardless of the values of the other attributes.
If you want to collect the value of the country attribute, you could write:
def match_asian_countries_pos(): results = []

```
for city in cities: match city:
                case City('Asia', _, country):
                    results.append(country)
return results
```
