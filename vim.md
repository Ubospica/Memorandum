### show hex
:%!xxd

### trans to crlf/cr/lf
:set ff=unix/dos/mac
:e ++ff=unix #only view in unix mode
unix(linux/macos): lf
dos(windows):crlf
mac(old macos):cr
