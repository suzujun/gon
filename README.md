# gon

## Installation
Once you have [installed Go][golang-install], run these commands
to install the `gon` tool:
```bash
$ go get github.com/suzujun/gon
```

## Running gon

Example:

	gon slice -source=foo.go [other options]

The `mockgen` command is used to generate source code for a slice
class.
It supports the following flags:

 *  `-source`: A file containing interfaces to be mocked.

 *  `-destination`: A file to which to write the resulting source code. If you
    don't set this, the code is printed to standard output.

 *  `-package`: The package to use for the resulting mock class
    source code. If you don't set this, the package name is `mock_` concatenated
    with the package of the input file.

## Generate Slice
[GitHub](http://github.com) [GitHub](http://github.com#111)

### Select[Type|FieldName]
_Alias: collect _

Returns a projected slice given a func which maps Example to T. Comparable to LINQ’s Select or underscore’s map.
Command:
```
gon slice Select[int]
gon slice Select[Points]
```
Signature:
```
func (ExampleSlice) Select{type|fieldName}(func(Example) type) []type
```
Example:
```golang:
// +gen slice:"Select[int],Select[Name]"
type Player struct {
	Name   string
	Points int
}
players := PlayerSlice {
	{"Alice", 450},
	{"Bob", 100},
	{"Carly", 200},
}

// select points for type
points := players.SelectInt(func(p Player) int {
	return p.Points * 10
}) // => [4500, 1000, 2000]

// select points for field name
players.SelectPoints() // => [450, 100, 200]
```

### GroupBy[Type|FieldName]
Signature:
```
func (ExampleSlice) GroupBy{type|fieldName}(func(Example) type) []type
```
### IndexBy[Type|FieldName]
Signature:
```
func (ExampleSlice) IndexBy{type|fieldName}(func(Example) type) []type
```
### SortBy
Signature:
```
func (ExampleSlice) SortBy(func(Example, Example) bool) ExampleSlice
```
### Filter
_Alias: Where_
Signature:
```
func (ExampleSlice) Filter(func(Example) bool) ExampleSlice
```
### Distinct
_Alias: Uniq,Unique_
Signature:
```
func (ExampleSlice) Distinct(func(Example) bool) ExampleSlice
```
### Reject
Signature:
```
func (ExampleSlice) Reject(func(Example) bool) ExampleSlice
```
### Every
Signature:
```
func (ExampleSlice) Every(func(Example) bool) ExampleSlice
```
### Find
Signature:
```
func (ExampleSlice) Find(func(Example) bool) ExampleSlice
```
### IndexOf
Signature:
```
func (ExampleSlice) IndexOf(func(Example) bool) uint
```
### LastIndexOf
Signature:
```
func (ExampleSlice) LastIndexOf(func(Example) bool) uint
```
### Without
Signature:
```
func (ExampleSlice) Without(...Example) ExampleSlice
```
### Difference
Signature:
```
func (ExampleSlice) Difference(ExampleSlice) ExampleSlice
```
### Shuffle
Signature:
```
func (ExampleSlice) Shuffle() ExampleSlice
```
### Sample
Signature:
```
func (ExampleSlice) Sample(int) ExampleSlice
```
### CountBy
Signature:
```
func (ExampleSlice) CountBy(func(Example) bool) uint
```
### Min
Signature:
```
func (ExampleSlice) Min(func(Example, Example) bool) Example
```
### Max
Signature:
```
func (ExampleSlice) Max(func(Example, Example) bool) Example
```
### Reduce
Signature:
```
func (ExampleSlice) Reduce(func(int, Example) int, int) Example
```
### Partition
Signature:
```
func (ExampleSlice) Partition(func(Example) bool) []ExampleSlice
```
