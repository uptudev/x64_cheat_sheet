# x64 Cheat Sheet


## x64 Registers

8-byte register | Byte 0-3 | Bytes 0-1 | Byte 0
----------------|----------|-----------|-------
%rax | %eax | %ax | %al
%rcx | %ecx | %cx | %cl
%rdx | %edx | %dx | %dl
%rbx | %ebx | %bx | %bl
%rsi | %esi | %si | %sil
%rdi | %edi | %di | %dil
%rsp | %esp | %sp | %spl
%rbp | %ebp | %bp | %bpl
%r8 | %r8d | %r8w | %r8b
%r9 | %r9d | %r9w | %r9b
%r10 | %r10d | %r10w | %r10b
%r11 | %r11d | %r11w | %r11b
%r12 | %r12d | %r12w | %r12b
%r13 | %r13d | %r13w | %r13b
%r14 | %r14d | %r14w | %r14b
%r15 | %r15d | %r15w | %r15b


## Operand Specifiers

###### Imm = constant value, E<sub>x</sub> = register, 
###### R[E<sub>x</sub>] = value stored in E<sub>x</sub>, M[x] = value stored at memory address

Type | From | Operand Value | Name
-----|------|---------------|-----
Immediate | $Imm | Imm | Immediate
Register | E<sub>2</sub> | R[E<sub>a</sub>]| Register
Memory | Imm | M[Imm]| Absolute
Memory | (E<sub>2</sub>) | M[R[E<sub>b</sub>]] | Absolute
Memory | Imm[E<sub>b</sub>, E<sub>i</sub> s] | M[Imm + R[E<sub>b</sub>] + (R[E<sub>i</sub>] x s) | Scaled Index


## Data Movement

###### b = byte, w = word, l = doubleword (4 byte integer), q = quadword (8 byte integer)
###### s = source, d = destination

Instruction | Description
------------|------------
One suffix |    
mov  *s, d* | Move source to destination
push *s* | Move source to stack
pop *d* | Pop top of stack to destination
Two suffixes | 
mov *s, d* | Move byte to word (zero extended)
push *s* | Move byte to word (zero extended)
No suffix |
cwtl | Convert word in *%ax* to doubleword in *%eax* (sign-extended)
cltq | Convert doubleword in *%eax* to quadword in *%rax* (sign-extended)
cqto | Convert quadword in *%rax* to octoword in *%rdx:%rax*

## System Calls
%rax|System Call|%rdi|%rsi|%rdx|%r10|%r8|%r9
---|---|---|---|---|---|---|---
0|sys_read|unsigned int fd|char *buf|size_t count|||
1|sys_write|unsigned int fd|const char *buf|size_t count|||
2|sys_open|const char *filename|int flags|int mode|||
3|sys_close|unsigned int fd|||||
4|sys_stat|const char *filename|struct stat *statbuf||||
5|sys_fstat|unsigned int fd|struct stat *statbuf||||
6|sys_lstat|fconst char *filename|struct stat *statbuf||||
7|sys_poll|struct poll_fd *ufds|unsigned int nfds|long timeout_msecs|||
8|sys_lseek|unsigned int fd|off_t offset|unsigned int origin|||
9|sys_mmap|unsigned long addr|unsigned long len|unsigned long prot|unsigned long flags|unsigned long fd|unsigned long off
10|sys_mprotect|unsigned long start|size_t len|unsigned long prot|||
11|sys_munmap|unsigned long addr|size_t len||||
12|sys_brk|unsigned long brk|||||
13|sys_rt_sigaction|int sig|const struct sigaction *act|struct sigaction *oact|size_t sigsetsize||
14|sys_rt_sigprocmask|int how|sigset_t *nset|sigset_t *oset|size_t sigsetsize||
15|sys_rt_sigreturn|unsigned long __unused|||||
16|sys_ioctl|unsigned int fd|unsigned int cmd|unsigned long arg|||
17|sys_pread64|unsigned long fd|char *buf|size_t count|loff_t pos||
18|sys_pwrite64|unsigned int fd|const char *buf|size_t count|loff_t pos||
19|sys_readv|unsigned long fd|const struct iovec *vec|unsigned long vlen|||
20|sys_writev|unsigned long fd|const struct iovec *vec|unsigned long vlen|||
21|||||||
22|||||||
23|||||||
24|||||||
25|||||||
26|||||||
27|||||||
28|||||||
29|||||||
30|||||||
31|||||||
32|||||||
33|||||||
34|||||||
35|||||||
36|||||||
37|||||||
38|||||||
39|||||||
40|||||||
41|||||||
42|||||||
43|||||||
44|||||||
45|||||||
46|||||||
47|||||||
48|||||||
49|||||||
50|||||||
51|||||||
52|||||||
53|||||||
54|||||||
55|||||||
56|||||||
57|||||||
58|||||||
59|||||||
60|||||||
61|||||||
62|||||||
63|||||||
64|||||||
65|||||||
66|||||||
67|||||||
68|||||||
69|||||||
70|||||||
71|||||||
72|||||||
73|||||||
74|||||||
75|||||||
76|||||||
77|||||||
78|||||||
79|||||||
80|||||||
81|||||||
82|||||||
83|||||||
84|||||||
85|||||||
86|||||||
87|||||||
88|||||||
89|||||||
90|||||||
91|||||||
92|||||||
93|||||||
94|||||||
95|||||||
96|||||||
97|||||||
98|||||||
99|||||||
100|||||||
101|||||||
102|||||||
103|||||||
104|||||||
105|||||||
106|||||||
107|||||||
108|||||||
109|||||||
110|||||||
111|||||||
112|||||||
113|||||||
114|||||||
115|||||||
116|||||||
117|||||||
118|||||||
119|||||||
120|||||||
121|||||||
122|||||||
123|||||||
124|||||||
125|||||||
126|||||||
127|||||||
128|||||||
129|||||||
130|||||||
131|||||||
132|||||||
133|||||||
134|||||||
135|||||||
136|||||||
137|||||||
138|||||||
139|||||||
140|||||||
141|||||||
142|||||||
143|||||||
144|||||||
145|||||||
146|||||||
147|||||||
148|||||||
149|||||||
150|||||||
151|||||||
152|||||||
153|||||||
154|||||||
155|||||||
156|||||||
157|||||||
158|||||||
159|||||||
160|||||||
161|||||||
162|||||||
163|||||||
164|||||||
165|||||||
166|||||||
167|||||||
168|||||||
169|||||||
170|||||||
171|||||||
172|||||||
173|||||||
174|||||||
175|||||||
176|||||||
177|||||||
178|||||||
179|||||||
180|||||||
181|||||||
182|||||||
183|||||||
184|||||||
185|||||||
186|||||||
187|||||||
188|||||||
189|||||||
190|||||||
191|||||||
192|||||||
193|||||||
194|||||||
195|||||||
196|||||||
197|||||||
198|||||||
199|||||||
200|||||||
201|||||||
202|||||||
203|||||||
204|||||||
205|||||||
206|||||||
207|||||||
208|||||||
209|||||||
210|||||||
211|||||||
212|||||||
213|||||||
214|||||||
215|||||||
216|||||||
217|||||||
218|||||||
219|||||||
220|||||||
221|||||||
222|||||||
223|||||||
224|||||||
225|||||||
226|||||||
227|||||||
228|||||||
229|||||||
230|||||||
231|||||||
232|||||||
233|||||||
234|||||||
235|||||||
236|||||||
237|||||||
238|||||||
239|||||||
240|||||||
241|||||||
242|||||||
243|||||||
244|||||||
245|||||||
246|||||||
247|||||||
248|||||||
249|||||||
250|||||||
251|||||||
252|||||||
253|||||||
254|||||||
255|||||||
256|||||||
257|||||||
258|||||||
259|||||||
260|||||||
261|||||||
262|||||||
263|||||||
264|||||||
265|||||||
266|||||||
267|||||||
268|||||||
269|||||||
270|||||||
271|||||||
272|||||||
273|||||||
274|||||||
275|||||||
276|||||||
277|||||||
278|||||||
279|||||||
280|||||||
281|||||||
282|||||||
283|||||||
284|||||||
285|||||||
286|||||||
287|||||||
288|||||||
289|||||||
290|||||||
291|||||||
292|||||||
293|||||||
294|||||||
295|||||||
296|||||||
297|||||||
298|||||||
299|||||||
300|||||||
301|||||||
302|||||||
303|||||||
304|||||||
305|||||||
306|||||||
307|||||||
308|||||||
309|||||||
310|||||||
311|||||||
312|||||||
313|||||||
314|||||||
315|||||||
316|||||||
317|||||||
318|||||||
319|||||||
320|||||||
321|||||||
322|||||||
323|||||||
324|||||||
325|||||||
326|||||||
327|||||||
328|||||||
329|||||||
330|||||||
331|||||||
332|||||||
333|||||||
334|||||||
335|||||||


## Arithmetic Operations

### Unary Operations

Instruction | Description
------------|------------
inc *d* | Increment by 1
dec *d* | Decrement by 1
neg *d* | Arithmetic negation
not *d* | Bitwise complement

### Binary Operations

Instruction | Description
------------|------------
leaq *s, d* | Load effective address of source into destination
add *s, d* | Add source to destination
sub *s, d* | Subtract source from destination
imul *s, d* | Multiply source by destination
xor *s, d* | Bitwise XOR (exclusive or) destination by source
or *s, d* | Bitwise OR destination by source
and *s, d* | Bitwise AND destination by source

### Shift Operations

Instruction | Description
------------|------------
sal/sdl *k, d* | Left shift destination by *k* bits
sar *k, d* | Arithmetic right shift by *k* bits
shr *k, d* | Logical right shift by *k* bits

### Special Arithmetic Operations

Instruction | Description
------------|------------
imulq *s* | Signed full multiply of *%rax* by *s*, result stored in  *%rdx*:*%rax*
mulq *s* | Unsigned full multiply of *%rax* by *s*, result stored in  *%rdx*:*%rax*
idivq *s* | Signed divide *%rdx*:*%rax* by *s*, quotient stored in *%rax*, remainder stored in *rdx*
divq *s* | Unsigned divide *%rdx*:*%rax* by *s*, quotient stored in *%rax*, remainder stored in *rdx*


## Comparisons and Tests

Instruction | Description
------------|------------
cmp *s<sub>2</sub>*, *s<sub>1</sub>* | Set condition codes according to *s<sub>1</sub>* - *s<sub>2</sub>*
test *s<sub>2</sub>*, *s<sub>1</sub>* | Set condition codes according to *s<sub>1</sub>* - *s<sub>2</sub>*

## Condition Codes

### Conditional Set Instructions

Instruction | Description | Condition Code
------------|-------------|---------------
sete/setz *D* | Set if equal/zero | **ZF**
setne/setnz *D* | Set if not equal/nonzero | **~ZF**
sets *D* | Set if negative | **SF**
setns *D* | Set if nonnegative | **~SF**
setg/setnle *D* | Set if greater (signed) | **~(SF^0F)&~ZF**
setge/setnl *D* | Set if greater or equal (signed) | **~(SF^0F)**
setl/setnge *D* | Set if less (signed) | **SF^0F**
setle/setng *D* | Set if less or equal | **(SF^0F)|ZF**
seta/setnbe *D* | Set if above (unsigned) | **~CF&~ZF**
setae/setnb *D* | Set if above or equal (unsigned) | **~CF**
setb/setnae *D* | Set if below (unsigned) | **CF**
setbe/setna *D* | Set if below or equal (unsigned) | **CF** or **ZF**


### Jump Instructions

Instruction | Description | Condition Code
------------|-------------|---------------
jmp | Jump to label | 
jmp *operand* | Jump to specified location
je/jz | Jump if equal/zero | **ZF**
jne/jnz | Jump if not equal/zero | **~ZF**
js | Jump if negative | **SF**
jns | Jump if nonnegative | **~SF**
jg/jnle | Jump if greater (signed) | **~(SF^0F)&~ZF**
jge/jnl | Jump if greater or equal (signed) | **~(SF^0F)**
jl/jnge | Jump if less (signed) | **SF^0F**
jle/jng | Jump if less or equal | **(SF^0F)|ZF**
ja/jnbe | Jump if above (unsigned) | **~CF&~ZF**
jae/jnb | Jump if above or equal (unsigned) | **~CF**
jb/jnae | Jump if below (unsigned) | **CF**
jbe/jna | Jump if below or equal (unsigned) | **CF** or **ZF**


### Conditional Move Instructions

Instruction | Description | Condition Code
------------|-------------|---------------
cmove/cmovz *S, D* | Move if equal/zero | **ZF**
cmovne/cmovnz *S, D* | Move if not equal/nonzero | **~ZF**
cmovs *S, D* | Move if negative | **SF**
cmovns *S, D* | Move if nonnegative | **~SF**
cmovg/cmovnle *S, D* | Move if greater (signed) | **~(SF^0F)&~ZF**
cmovge/cmovnl *S, D* | Move if greater or equal (signed) | **~(SF^0F)**
cmovl/cmovnge *S, D* | Move if less (signed) | **SF^0F**
cmovle/cmovng *S, D* | Move if less or equal | **(SF^0F)|ZF**
cmova/cmovnbe *S, D* | Move if above (unsigned) | **~CF&~ZF**
cmovae/cmovnb *S, D* | Move if above or equal (unsigned) | **~CF**
cmovb/cmovnae *S, D* | Move if below (unsigned) | **CF**
cmovbe/cmovna  *S, D* | Move if below or equal (unsigned) | **CF** or **ZF**  


### Procedure Call Instructions

Instruction | Description 
------------|-------------
call *label* | Push return address and jump to label
call *operand* | Push return address and jump to specified location
leave | Set **%rsp** to **%rbp**, then pop top of stack to **%rbp**
ret | Pop return address from stack and jump there
