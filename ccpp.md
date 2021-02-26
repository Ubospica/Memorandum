c++

## C++ style IO
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

### member func
`istream.get() get(char&)`: get a char; the first returns a int val(possibly -1)
`istream.get(char*,uint,char='\n')`: get str; not extract the char
`istream.getline(char*,uint,char='\n')`: get str; extract & discard the char
`getline(istream,string,char='\n')`
`is.unget()`
`is.ignore(uint=1,char=EOF)` ignore char len=$1 (delim included) or char=$2 (extract & discard char)
`is.read(char*,int), os.write(char*,uint)`: binary file operation
`os.put()`
`os.flush() = os<<std::flush`

### filestream
`fstream(),fstream(string),fstream(char*),fstream(string,mode)`
`f.open(),f.close(),f.is_open()`: open fail:failbit; succ:clear()
`~fstream()`: auto close

fstream::in
fstream::out
fstream::app
fstream::ate
fstream::trunc
fstream::binary
read: in
write: out out|trunc out|app(=app)
out only:=out|trunc; create file
ate,binary always OK to use

### position
`ios_base::beg`
`ios_base::end`
`ios_base::cur`

### stringstream:
`str()`: returns a temporary string
`str(str)` set str; not clear iostate

### binary
`f(string, state|ios::binary)`
`f.tellg(), f.tellp(), f.seekg(), f.seekp()`
`f.read(reinterpret_cast<char*>(&x), sizeof(x))`
`f.write(reinterpret_cast<char*>(&x), sizeof(x))`
`f.flush(), f.close()`

### other
check if empty:  
`s.peek() != EOF` or  
`s.rdbuf()->in_avail()`  
EOF:  
`char_traits<char>::eof()`

boolalpha



