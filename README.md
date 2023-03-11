## Encoded/Decode hexadecimal in V
### Example
```v
import hex

pub struct Person {
	age int
	name string
	gender Gender
	eye_color string
	hair_color string
	weight u16
}

enum Gender {
	male
	female
}

fn main() {
	str := 'V is awesome'
	println('SOURCE: ${str}')
	println('ENCODED: ${hex.encode(str)}')
	println('DECODED: ${hex.decode(hex.encode(str)) or {"failed"}}')

	p := Person{21, 'Adam', .male, 'hazel', 'brown', 100}
	enc := hex.encode_struct(p) or { 'failed'.bytes() }
	println('STRUCT ENCODED: ${enc.bytestr()}')
	dec := hex.decode_struct<Person>(enc) or {
		println(err.msg())
		exit(0)
	}
	println('STRUCT DECODED: ${dec}')
}
```