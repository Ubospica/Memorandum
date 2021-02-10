c++

## usage of stream
### state
ios_base::badbit = 1 stream collapse
ios_base::eofbit = 2 stream end
ios_base::failbit = 4 input format err or io fail
eof() 
fail() returns badbit|failbit is true
bad()
setstate() preserve the bit & add new bit
rdstate() get bit
clear()
clear(bit) clear bit & set
operator bool = !fail()

### tie
a.tie(b): flush b before i/o of a
`tie()` return cur (no tie:null)
`tie(ostream*)` return cur & set cur (null: no tie)

cerr: associated with stderr; tie with cout; auto flush
clog: not tie with cout; not auto flush

### filestream
`fstream(),fstream(string),fstream(char*),fstream(string,mode)`
`f.open(),f.close(),f.is_open()`: open fail:failbit; succ:clear()
`~fstream()`: auto close

mode:
in: ion


check if empty:  
`s.peek() != EOF` or  
`s.rdbuf()->in_avail()`  
EOF:  
`char_traits<char>::eof()`

stringstream:
`str()`: returns a temporary string
`str(str)` set str; not clear iostate


boolalpha
