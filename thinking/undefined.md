# 요청이 무한대로 들어오면 어떻게 될까?



```text
<--- Last few GCs --->

[87018:0x102aba000]    60172 ms: Scavenge 1977.3 (1981.6) -> 1976.6 (1983.3) MB, 33.9 / 0.1 ms  (average mu = 0.326, current mu = 0.328) allocation failure
[87018:0x102aba000]    60243 ms: Scavenge 1978.6 (1983.3) -> 1978.0 (1984.1) MB, 49.0 / 0.1 ms  (average mu = 0.326, current mu = 0.328) allocation failure
[87018:0x102aba000]    60296 ms: Scavenge 1979.8 (1984.1) -> 1979.2 (1985.1) MB, 34.0 / 0.1 ms  (average mu = 0.326, current mu = 0.328) allocation failure


<--- JS stacktrace --->

==== JS stack trace =========================================

    0: ExitFrame [pc: 0x10097cc39]
Security context: 0x33a8e46808d1 <JSObject>
    1: test [0x33a8fe125669] [/Users/bugtype/Downloads/test.js:~6] [pc=0x2b1b882cbf10](this=0x33a87ce3ff49 <JSGlobal Object>)
    2: _onTimeout [0x33a8da435b99] [/Users/bugrype/Downloads/test.js:26] [bytecode=0x33a87427b4e1 offset=5](this=0x33a8da435ab9 <Timeout map = 0x33a8fcfc2b99>)
    3: listOnTimeout(aka listOnTimeout) [0x33a810340119] [internal/timers.js:549] [byteco...

FATAL ERROR: Ineffective mark-compacts near heap limit Allocation failed - JavaScript heap out of memory
 1: 0x1010285f9 node::Abort() (.cold.1) [/usr/local/bin/node]
 2: 0x10008634d node::FatalError(char const*, char const*) [/usr/local/bin/node]
 3: 0x10008648e node::OnFatalError(char const*, char const*) [/usr/local/bin/node]
 4: 0x100187c07 v8::Utils::ReportOOMFailure(v8::internal::Isolate*, char const*, bool) [/usr/local/bin/node]
 5: 0x100187ba7 v8::internal::V8::FatalProcessOutOfMemory(v8::internal::Isolate*, char const*, bool) [/usr/local/bin/node]
 6: 0x100315955 v8::internal::Heap::FatalProcessOutOfMemory(char const*) [/usr/local/bin/node]
 7: 0x1003171ca v8::internal::Heap::RecomputeLimits(v8::internal::GarbageCollector) [/usr/local/bin/node]
 8: 0x100313bfc v8::internal::Heap::PerformGarbageCollection(v8::internal::GarbageCollector, v8::GCCallbackFlags) [/usr/local/bin/node]
 9: 0x1003119fe v8::internal::Heap::CollectGarbage(v8::internal::AllocationSpace, v8::internal::GarbageCollectionReason, v8::GCCallbackFlags) [/usr/local/bin/node]
10: 0x100310a41 v8::internal::Heap::HandleGCRequest() [/usr/local/bin/node]
11: 0x1002d5ce1 v8::internal::StackGuard::HandleInterrupts() [/usr/local/bin/node]
12: 0x10063de0c v8::internal::Runtime_StackGuard(int, unsigned long*, v8::internal::Isolate*) [/usr/local/bin/node]
13: 0x10097cc39 Builtins_CEntry_Return1_DontSaveFPRegs_ArgvOnStack_NoBuiltinExit [/usr/local/bin/node]
```

무한히 늘려서 테스트 해보았다. 당연히  에러가 나는 것을 알았는데 어떤 에러인지는 추측이 안되었다.

```text
FATAL ERROR: Ineffective mark-compacts near heap limit Allocation failed - JavaScript heap out of memory
```

에러를 확인해보니 힙이 할당할 수 있는 영역이 넘었기 때문에 안된다.

* 추가적으로 관련자료를 찾아보니, Event loop안에는 6개의 queue가 있는 것은 위에서 설명하였다. 해당 queue는 동적으로 늘어난다고 한다. heap 사이즈 만큼.







