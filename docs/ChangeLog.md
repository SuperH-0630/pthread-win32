2021-08-16  Ingo
----------


* Makefile (install target): add checks for file existance.
* README: fix some out of date instructions or descriptions.




2021-04-13
----------

			
* (c3e68f2) rename docs to .md to have them render as MarkDown files in GitHub (easier to read)
			
* (b43f651) remove superfluous resource files

  update MSVC project files to point at the sources again (after the MSVC project files were moved into the windows/VS20XX/ directory tree)
			
* (9c124bd) bump version to 2.10.2
			
* (046928e) augmented all mutex tests to properly clean up the mutexes and mutex attributes.
			
* (4c80f6f) added feature (undocumented): `pthread_kill(t, SIGABRT)` can now be used to kill a deadlocked (stuck) thread. This was previously NOT possible and caused the test wrapper to deadlock at the end: it would run all tests but never terminate.
  
  I guess that "ALL TESTS PASS' statement a few commits ago was a bit overzealous  :'-(
			
* (d563bbc) add new tests: thread cancelation point showcase and pthread_kill basic test
			
* (d979315) add missing tests

  add the setup/destroy logic to each test call in the wrapper to help improve test stability across the board.
			
* (be4757e) cancel8 remains the most finicky test of all.   **ALL TESTS PASS**
			
* (f7e8a9f) correct wording to prevent confusion about the announcement message in the test
			
* (b886906) fix fatal bug in semaphore3 test: off-by-1 error in cleanup/join loop resulted in a crash due to invalid memory access attempt at the t[0] slot, which is uninitialized (intentionally).
			
* (318df6b) correct MSVC project target names to suit loadlibrary test: the DLL will be called `pthread.dll` instead of `pthread_dll.dll`, while the static library will be named `pthread_static_lib.lib` to prevent confusion with the DLL "import library" `pthread.lib` which the linker will produce neext to the `pthread.dll` target file.
			
* (f42f382) fix for exception2 test: when the thread raises an exception, abort the thread and flag it as canceled, just like we do in the setjmp/longjmp variant: abort the thread but DO NOT YET abort the application.
			
* (6f64d60) fixed a couple of compiler warnings
			



2021-04-03
----------

			
* (17a7464) changed from using mongoose to civetweb webserver (it's MIT fork after it went the whole GNU)
			



2021-03-18
----------

			
* (e70d6a5) init all variables from global.c in global.c
			
* (625eeb2) ptw32_processInitialize before cleanup
			



2021-03-16
----------

			
* (a9a6d55) Update pthread.c
			
* (53f3d7b) _strdup -> ptw32_strdup
			



2021-03-15
----------

			
* (c097e1c) remove obnoxious compiler warning; this will declare VERY LONG timeout…
			
* (fcbcf8a) undef PTW32_STATIC_LIB for MSVS builds if and only if _WINDLL is defined(dll build)
			



2021-02-25
----------

			
* (034d9bd) remove obnoxious compiler warning; this will declare VERY LONG timeouts (> 2E6 seconds) on 32-bit builds illegal (EINVAL)
			



2021-02-07
----------

			
* (1e5e82e) fix manual merge mistake
			
* (7837928) fix bungled commit SHA-1: 4675ec485184efec8c77fc040c98b23c317bdfd1 :: migrated to MSVC2019
  
  Make sure the 2013 & 2015 project files remain unchanged, i.e. REVERTING them to their original state now.
			
* (280a346..e672657) added MSVC2019 project files
			
* (8052a62) fixed fatal error in MSVC2019
			
* (4675ec4) migrated to MSVC2019
			



2021-01-13
----------

			
* (ee0ccdc..3eb3806) Update pthread_win32_attach_detach_np.c
			



2020-12-30
----------

			
* (77bbbf2) Update ptw32_throw.c
  
  deferencing pointer fix
			



2020-11-04
----------

			
* (9361387) fix warning
			



2020-10-27
----------

			
* (c1f38ad) fixed old c-style declaration errors
			
* (a229f3c) fixed static analysis errors
			



2020-07-06
----------

			
* (7b1cf19) Updated project to VS2019 and removed redundant .VS2017 suffix
			
* (3573556) Removed line since see no need to enable switches
			
* (eea3c89) Combined Readme and added changes to readme


			



2019-11-03
----------

2019-11-03  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* NOTICE: Remove third party code acknowledgments because files have been
	removed from distro.

			

			



2019-09-10
----------

			
* (46515ab) Fixed slow build, multiple symbol issue due to double *.c list, fixed macro redefinition warnings.
			
* (f9d2d14) fix: public interface pthread.h, sched.h, semaphore.h
			
* (98a45e5) Added CMakeLists.txt and mamafile.py for use with MAMA build tool
			



2019-07-30
----------

			
* (9ff8b06) Revert "Update w32_CancelableWait.c"
  
  This reverts commit bf0e247aed35f05c5853cb630c716e3604c6e10e.
			
* (ef31ba8) Revert "Update sem_timedwait.c"
  
  This reverts commit f3ffb80a4c3805333abb9e27766de62a78a4d1ff.
			
* (f3ffb80) Update sem_timedwait.c
  
  check if milliseconds delay had expired
			
* (bf0e247) Update w32_CancelableWait.c
  
  check if timeout has expired already before call to WaitForMultipleObjects
			



2019-06-27
----------

			
* (2a5245a) Update implement.h
			



2019-05-24
----------

			
* (efe335b) -
			



2019-05-03
----------

			
* (1ed67a4) support uwp platform





2018-08-19
----------

2018-08-19  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* context.h (PTW32_PROCPTR): Added missing '__' prefix for v3.

			



2018-08-13
----------

			
* (85f21e7) pthread for windows updated

			



2018-08-10
----------

2018-08-10  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile (clean): remove *.idb files.
	* dll.c: replace 'extern "C"' with macros PTW32_BEGIN_C_DECLS/PTW32_BEGIN_C_DECLS
	for consistency tidy-up; add comment re ptw32_autostatic_anchor() function;
	make our static constructor/destructors "extern" to avoid optimisers.
	* implement.h (ptw32_autostatic_anchor): add PTW32_BEGIN_C_DECLS/PTW32_BEGIN_C_DECLS
	envelope.

			



2018-08-08
----------

2018-08-08  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile: "nmake realclean VC VC-static" and similar wasn't remaking pthread.obj.
	* common.mk: changes to accommodate the above.
	* GNUmakefile: use changes in common.mk but still has problem with
	"make realclean GC GC-static" and similar.
	* configure.ac (AC_INIT): package name change.

2018-08-08  Mark Pizzolato <markpizzolato dash pthreads dash win32 at subscriptions dot pizzolato dot net>

	* config.h (NEED_FTIME): Removed
	* _ptw32.h (NEED_FTIME): Removed.
	* ptw32_timespec.c (NEED_FTIME): Removed conditional.
	* ptw32_relmillisecs: Fix long-standing bug in NEED_FTIME code; remove NEED_FTIME
	and all !NEED_FTIME code; compare nanoseconds and convert to milliseconds
	at the end.
	* implement.h (NEED_FTIME): remove conditionals.
	* pthread.h: Remove Borland compiler time types no longer needed.
	* configure.ac (NEED_FTIME): Removed check.
	
			



2018-08-07
----------

2018-08-07  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* GNUmakefile.in (DLL_VER): rename as PTW32_VER.
	* Makefile (DLL_VER): Likewise.
	* Bmakefile (DLL_VER): Likewise; does anyone use this anymore?
	* pthread.h: Move internal library stuff from pthread.h to _pthw32.h
	* _ptw32.h: As above.
	* ANNOUNCE: Update.
	* NEWS: Update.
	* Makefile: Static libraries renamed to libpthreadV*

			



			



2018-07-25
----------

			
* (89d7bd5..8d58eb2) Added VS2015 project files.





2018-07-22
----------

2018-07-22  Mark Pizzolato <markpizzolato dash pthreads dash win32 at subscriptions dot pizzolato dot net>

	* _ptw32.h: Restore support for compiling as static (with /MT or /MTd);
	define int64_t and uint64_t as typedefs rather than #defines.
	* dll.c: Likewise.
	* implement.h: Likewise.
	* need_errno.h: Likewise.
	* pthread_detach.c: Likewise.

2018-07-22  Carlo Bramini <carlo underscore bramini at users dot sourceforge dot net>

	* context.h (ARM): Additional macros checked for ARM processors.

2018-07-22  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile (all-tests-md): New; run the /MD build and tests from
	all-tests-cflags.
	* Makefile (all-tests-mt): New; run the /MT build and tests from
	all-tests-cflags.
	* Makefile (all-tests-cflags): retain; require all-tests-md and
	all-tests-mt.
	
			



2018-04-24
----------

			
* (5e8d630) add msvc2017
			



2017-06-05
----------

			
* (8597c27) added project files for Visual Studio 2017
    updated PlatformToolset to v141
  added project files for pthread_lib_static - also for 2017,
    for full static compilation
    using PlatformToolset to v141_xp
  
  Signed-off-by: hayati ayguen <h_ayguen@web.de>
			






2016-12-25
----------

2016-12-25  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Change all license notices to the Apache License 2.0
	* LICENCE: New Apache License file
	* NOTICE: New file.
	* COPYING: Removed.
	* COPYING.GPL: Removed.






2016-12-20
----------

2016-12-20  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* implement.h (PThreadStateReuse): this thread state enum value
	must be less than PThreadStateRunning to reflect an invalid thread
	handle.
	* pthread_kill.c: changed conditions for return of ESRCH.
	* ptw32_destroy.c: copy HANDLEs rather than whole thread struct;
	edit comment.
	* pthread_self.c: set implicit thread handle state to PThreadStateRunning.
	* pthread_create.c: set thread state to PThreadStateSuspended
	regardless because it must have state >= PThreadStateRunning on return.

2016-12-20  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* all (PTW32_*): rename to PTW32_*.
	(ptw32_*): rename to ptw32_*.
	(PtW32*): rename to __PtW32*.
	* pthread.h (PTW32_VERSION_MAJOR): = 3
	(PTW32_VERSION_MINOR): = 0
	* GNUmakefile: removed; must now configure from GNUmakefile.in.
	I.e. For either MinGW or MinGW-w64:
		# autoheader
		# autoconf
		# ./configure
	* pthread.h (PTHREAD_ONCE_INIT): for PTW32_VERSION_MAJOR > 2,
	reverse element values to conform to new pthread_once_t.






2016-12-18
----------

2016-12-18  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* implement.h  (PTW32_TEST_SNEAK_PEEK): Defined in tests/test.h
	to control what some tests see when sneaking a peek inside this
	header.
	* GNUMakefile.in: call tests "make realclean"





2016-12-17
----------

2016-12-17  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* _ptw32.h: MINGW(all) include stdint.h to define all specific
	size integers (int64_t etc).
	
2016-12-17  Kyle Schwarz <kyle dot r dot schwarz at gmail dot com>

	* _ptw32.h: MINGW6464 define pid_t as __int64.
	




2016-04-01
----------

2016-04-01  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* _ptw32.h: Move more header stuff into here.
	* pthread.h: Move stuff from here into _ptw32.h.
	* implement.h: Likewise.
	* sched.h (struct timespec): Wrap with extra condition check.
	* pthread_win32_attach_detach.c: Source stdlib.h to define
	_countof et. al.





2016-03-31
----------

2016-03-31  Keith Marshall <MinGW32 project>

	* aclocal.m4: New from MinGW32 patches for autoconf.
	* configure.ac: Likewise.
	* GNUmakefile.in: Likewise.
	* install-sh: Likewise.
	* _ptw32.h: Likewise.
	* implement.h: Patched.
	* pthread.h: Patched.
	* sched.h: Patched.
	* sem_open.c: Patched.
	* semaphore.h: Patched.
	* pthread_self.c: Patched.





2016-03-28
----------

2016-03-28  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* ptw32_relmillisecs.c (pthread_win32_getabstime_np): New
	platform-aware function to return the current time plus optional
	offset.
	* pthread.h (pthread_win32_getabstime_np): New exported function.
	* ptw32_timespec.c: Conditionally compile only if NEED_FTIME config
	flagged.
	* sched.h: Update platform config flags for applications.
	* semaphore.h: Likewise.
	* pthread.h: Likewise.




2016-03-25
----------


2016-03-25  Bill Parker <wp02855 at gmail dot com>

	* pthread_mutex_init.c: Memory allocation of robust mutex element
	was not being checked.




2016-02-29
----------
	
2016-02-29  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* GNUmakefile (MINGW_HAVE_SECURE_API): Moved to config.h. Undefined
	for __MINGW32__; remove (make optional) forcing a specific C std.
	* implement.h (uint64_t): Define for Visual Studio.

2016-02-29	Keith Marshall <keithmarshall at users dot sourceforge dot net>

	* ptw32_timespec.c: Fix C90 warnings from GCC; int64_t -> uint64_t




2016-02-18
----------

2016-02-18	Carey Gister <careygister at outlook dot com>

	* dll.c (DllMain): Should not be defined for static library builds.
	Doing so prevents static linking with a dll library.




2015-11-01
----------

2015-11-01	Anurag Sharma <anurags at fb dot com>

	* ptw32_MCS_lock.c: Fix a race condition causing crashes.
	This race condition was also analysed and reported with a slightly
	different fix independently by Jonathan Brown at VMware.

2015-11-01	Mark Smith <masmith at fb dot com>

	* ptw32_relmillisecs.c: Fix erroneous 0-time waits, symptomizing as
	busy-spinning eating CPU. When the time to wait is specified to be less
	than 1 millisecond were erroneously rounded down to 0; Modify WinCE
	dependency.
	* ptw32_timespec.c: Remove NEED_FTIME conditionality.




2015-10-20
----------

			
* (19fd505..ede13ec) added `.gitattributes` to prevent further CRLF issues -- at least with most files -- when working on the sources on multiple platforms.
			
* (9d49293) line ending
			



2015-09-06
----------

			
* (f790535) change msvc config after merge
			



2015-09-03
----------

			
* (a1b1420) Fix dll compilation issue for Visual Studio using makefile
  
  The compilation sanity checks in dll.c are expecting _WINDLL to be
  defined. In the Visual Studio project this definition is inherited
  but is not present when building using the makefile. As _WINDLL is
  referenced no where in the project other than the sanity checks it
  seems safe to define it via the makefile.
  
  This resolves #5.
			



2015-08-30
----------

			
* (07100a0) correcting tests
			
* (7953fbb) Added  MSVS2015 Solution + fix for MSVC2015
			
* (324b4e2) Fix use after free() and double free()
			



2015-08-21
----------

			
* (c07fbcb) correcting tests
			



2015-08-04
----------

			
* (e416712) Remove email address
			



2015-07-31
----------

			
* (a79a060) Remove double free when NEED_SEM is defined.
			



2015-07-29
----------

			
* (0a37afd) Fix use after free() and double free()




2015-06-31
----------

2015-06-31  Dimitry <>

	* sem_init.c: Remove double free() when NEED_SEM defined (for
	early versions of WinCE).
			



2015-05-07
----------

			
* (950f452) Added  MSVS2015 Solution + avoid defining snprintf while compiling under VS2015, as the function is already available
			



2015-04-23
----------

			
* (8134f2e) Email address change
			



2015-03-18
----------

			
* (74c382b) 
  - fix merge mistake in PthreadState enum
  
  - fix global find&replace for cancelation->cancellation: ptw32_RegisterCancellation() now has the proper case once again.
			
* (fac9c1c) fix merge: delete superfluous files that came in from the merge...
			
* (2c7a08a) fix MSVC2013 build (probably also erroneous in the MSVC2012 environment, but haven't got MSVC2012 installed on the current dev box :-( )
			
* (4e5d42e) created MSVC2013 projects/solution files (ported from MSVC2012)
			
* (c2410d6) adding the affinity tests (and other missing tests) to the monolithic wrapper
			



2015-02-03
----------

			
* (f9e636d..de6cc3d) Fix documentation HREF URLs. Fix HEAD sections; TITLE corrections and editor META tag removal
			



2014-07-22
----------

			
* (8f38a5f) Wait for threads to complete before exiting main()
			



2014-05-29
----------

			
* (b73b3a6) Part of removing autostatic.c
			
* (8b00512) Merge autostatic.c into dll.c;



2014-05-29  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* autostatic.c: Move content to dll.c so autostatic no longer required.
	* dll.c: Include content from autostatic.c.
	* pthread.c (autostatic.c): Remove #include.
	* common.mk (autostatic.*): remove from builds.
	* Makefile (realclean): delete make.log.txt if present.
	* GNUMakefile (realclean): Likewise.

			



2014-05-28
----------

			
* (80f6485) Fix a possible memory leak.



2014-05-28  Jaeeun Choi <jaeeun at mdstec dot com>

	* pthread_mutex_init.c: Check and free malloced robustNode element if
	init is returning an ENOSPC error.
			



2013-12-12
----------

			
* (1cfedb2) Fix conditional compilation.



2013-12-10
----------

2013-12-10  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile (*-small-static): Removed all small-static targets in the MS
	toolchain builds due to	failures of TLS in apps linked with these
	library builds, specifically fails tests/semaphore3.c. The other static
	builds pass this test.
	* dll.c: Remove unused MinGW static linking hooks; See autostatic.c.
	Hope to incorporate a working set of hooks here for gcc that supports
	PIMAGE_TLS_CALLBACK later at which point autostatic.c will be required
	only for older compilers.
			



2013-12-09
----------

			
* (3c2e21b) Update for VS 2013 Express cross tools (x64)



2013-12-09  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile (.rc.res): Add logic to extract target CPU from different
	environments.

			



2013-12-02
----------

			
* (7af80e6) Add _np functions missing from non-portable section
			



2013-11-13
----------

			
* (6dc36b1) Add missing function description.
			
* (8f9d90c) Test library reinitialisation within the same process.
			



2013-11-08
----------

			
* (3280dfb) Allow library to be reinitialised.
			



2013-09-13
----------

			
* (f4ab7c0) Cast for warning
			
* (0e13e9a) Type casts and warning fix for GCC
			
* (f3ebd1d) New test case to confirm timeouts are working as expected.
			



2013-09-12
----------

			
* (df19775) PTW32_LEVEL and PTW32_SCHED_LEVEL was multiply defined if
  _POSIX_C_SOURCE >= 200112L
			



2013-07-23
----------

			
* (1f494c4) Fixes relating to WINCE non-support for CPU affinity



2013-07-23  Keith Clanton <keith dot clanton at cloudcar dot com>

	* create.c: Don't apply cpu affinity from thread attributes for WINCE;
	bug fix.
	
2013-07-23  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* config.h (HAVE_CPU_AFFINITY): Defined.
	* several (WINCE): Substitute HAVE_CPU_AFFINITY where appropriate.

			



2013-07-17
----------

			
* (180aa00) Support older MSVCRT.DLLs



2013-07-17  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_getname_np.c: Replace strncpy_s with strncpy to support older
	MSVCRT.DLLs.
	* pthread_attr_getname_np.c: Likewise.


			



2013-07-03
----------

			
* (f61257f) Add tests/threestage.c to Copyright exceptions list
			
* (b191e75) define 'max' if not defined
			



2013-07-02
----------

			
* (da8cee2) Cast values from malloc/calloc
			
* (63be0bc) Example code borrowed with permission.
			



2013-06-27
----------

			
* (f6a7acf) Add new general test
			
* (cc89c36) Supply default runtime arguments
			
* (c3ba36c) MSVC: change WIN32 to _WIN32 for recognition
			
* (3b7c788) Updated to version from book 4th edition
			
* (6a918c6) Initial version: borrowed from Johnson M Hart
			



2013-06-20
----------

			
* (db01337) Fix critical typo in change description of static linking dllMain
  functionality.
			
* (2961396) Thread name documentation.
			



2013-06-19
----------

			
* (b95f6ec..83b98f3) Set thread name.



2013-06-19  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_attr_init.c: Initialise thread name element.
	* create.c: Initialise thread name from attributes.





2013-06-13
----------

2013-06-13  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_setname_np.c: Initial version.
	* pthread_getname_np.c: Initial version.
	* pthread_attr_setname_np.c: Initial version.
	* pthread_attr_getname_np.c: Initial version.
	* pthread.h: Add new prototypes.
	* implement.h (pthread_attr_t_): Add "thrname" element.
	* (ptw32_thread_t): Add "name" element.
			



2013-06-06
----------

			
* (364131f) pthread_attr_[gs]etstackaddr() return ENOSYS consistent with the manual
  page.
  pthread_attr_[gs]etstacksize() have added precompiler condition but no
  change to behaviour, i.e. these functions are supported.
			
* (5531f8c) Comments.
			
* (1cd7325) Additional pthread_attr_[gs]etaffinity_np changes, including a new test
  case.
		


2013-06-06  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread.h (_POSIX_THREAD_ATTR_STACKADDR): Now set to -1. The API
	prototypes are defined but return ENOSYS; previously the addr value was
	stored in the attribute struct and retreivable but unused.
	* pthread_attr_setstackaddr.c: Should return ENOSYS rather than silently
	ignore the setting.
	* pthread_attr_getstackaddr.c: Likewise.
	* pthread_attr_getaffinity_np.c: Initial version.
	* pthread_attr_setaffinity_np.c: Initial version.





2013-06-05
----------

			
* (3621d04) Added pthread_attr_[sg]etaffinity_np routines.
			
* (32844ef) Static linking enhancement to add TLS running of thread detach logic
			



2013-05-15
----------

			
* (2324644) TLS Callback added to run thread exit processing when static linked
  (MSVC 8 or above)




2013-05-01
----------

2013-05-01  Andrew Chernow <achernow at gmail dot com>

	* dll.c: Add invocation of thread detach logic for static linked
	applications for MSVC8.0 or later builds.
			



2013-04-17
----------

			
* (9dff6a1) updated the MSVC2012 project file
			



2013-02-21
----------

			
* (3c24537) Add comments
			
* (72bf898) Additional WinCE fixes
			
* (66c7ac0) Preprocessor define change
			
* (c6ba6ea) Comment edits
			
* (93bc4dc) WinCE does not support thread CPU affinity API
			



2012-12-19
----------

			
* (6534c50) Add #include for _tcsncat_s()
			
* (831694b) Fix operations involving TCHAR.



2012-12-19  Jason Baker <jason underscore baker at symantec dot com>

	* pthread_win32_attach_detach_np.c (pthread_win32_process_attach_np):
	Fix function calls involving TCHAR.

			



2012-12-13
----------

			
* (7d0306e) Spelling fix
			



2012-11-13
----------

			
* (58e4930) fixing the MSVC project files: first phase.
			



2012-10-29
----------

			
* (52fef8f) Remove NULL arg checks
			
* (432aa62) Reduce Sleeps



2012-10-29  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* sem_destroy.c: Remove NULL argument checks. These are only useful
	to guard against some uninitialised arguments, not an invalid sem_t.
	* sem_wait.c: Likewise.
	* sem_post.c: Likewise.
	* sem_post_multiple.c: Likewise.
	* sem_timedwait.c: Likewise.
	* sem_trywait.c: Likewise.
	* ptw32_semwait.c: Likewise.


			



2012-10-28
----------

			
* (17893c1) sem_t internal state mutex changed to MCS lock.



2012-10-28  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* implement.h: sem_t_ replace internal state mutex with MCS lock.
	* sem_init.c: Rewrite to use MCS lock rather than mutex.
	* sem_destroy.c: Likewise.
	* sem_wait.c: Likewise.
	* sem_post.c: Likewise.
	* sem_post_multiple.c: Likewise.
	* sem_timedwait.c: Likewise.
	* sem_trywait.c: Likewise.
	* ptw32_semwait.c: Likewise.

			



2012-10-26
----------

			
* (6bcb606) WinCE changes.


2012-10-26	sicaf-- at hanmail dot net

	* error.c: For WinCE use a more specific cast.
	* implement.h: For WinCE don't include process.h.
	* pthread_win32_attach_detach_np.c: For WinCE don't restrict QUserEx.dll
	search to system path.
			



2012-10-24
----------

			
* (43976ea) Note the new bug fix.
			
* (2ffb96d) Bug fix in pthread_key_delete; new regression test for this bug.



2012-10-24  Stephane Clairet <Stephane dot Clairet at 4d dot com>

	* pthread_key_delete.c: Bug fix - move keylock release to after the
	while loop. (This bug first was introduced at release 2.9.1) 


			



2012-10-22
----------

			
* (de8a8dc) Move utility-specific option to where utility is defined if it's used
  via a variable, i.e. "objdump -p"; rename OBJDUMP variable to reflect
  this.
			
* (1e3c9b4) Fix windres target for static builds
			



2012-10-21
----------

			
* (4879733) Remove reliance on utility 'ls'
			



2012-10-19
----------

			
* (7b1f41c) windres target setting for static libs fixed
			
* (441f0f0) Dynamicify the windres target setting to match code object file
			



2012-10-16
----------

			
* (691340b) Makefile - remove SDK variables; GNUmakefile - add EXTRAVERSION



2012-10-16  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile: Remove SDK environment setting; now needs to be done
	explicitly before running any nmake.
	* GNUmakefile: Move per command-line ARCH setting to TESTS_ENV.

			



2012-10-14
----------

			
* (2740214) remove debug code which was used to analyze the crashes
			
* (ca09e4d) pthread_self: fix odd crashes in user code due to pthread lib being spooked by incorrect (too late) init
			
* (fa17700) Fix
			



2012-10-13
----------

			
* (52c6289) Windres target should not have a default
			



2012-10-12
----------

			
* (4b79582) Makefile cleanup
			
* (b6e7a8d) Yet more reworking
			
* (98a1b59) New function
			



2012-10-11
----------

			
* (cccd0f9..e838c15) makefile reworking; removed loadfree test.
			



2012-10-10
----------

			
* (08b5cbf) Daniel patch and reworking
			



2012-10-05
----------

			
* (911c14a) New test
			



2012-10-04
----------

			
* (ca78956) Add pthread_tryjoin_np to API
			
* (6505ec2) Minor clarification
			
* (b7bbdd4) completing the older cdecl fix: SHA-1: ae46f236d4c411485d4a3c2a0eecee88bbf55559
  
  * cdecl missing in functions which are passed to pthread_cleanup_push(): fixed -- matches type ptw32_cleanup_callback_t this way.
			
* (fbc667f) Update: _POSIX_* defines; ANNOUNCE, NEWS, README doco.
			
* (0d12032) defensive programming and typo fix
			
* (e088f4b) mingw define and static function fixes for the tests



2012-10-04  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_tryjoin_np.c: New API
	* pthread.c (pthread_try_join_np): Added.
	* common.mk (pthread_tryjoin_np): Added.
	* pthread.h (pthread_tryjoin_np): Added.
	* NEWS: Updated.
	* README: Updated.
	* ANNOUNCE: Updated.

			



2012-10-03
----------

			
* (3097d93) Remove target recommendation from help (no longer needed)
			
* (c72ec8d) Change reference to COPYING.LIB to COPYING.FSF
			
* (4d84d79) Update Copyright notices
			
* (c57a4d8) Initialise newmask to zero
			
* (83a488e) Comment edit
			



2012-10-02
----------

			
* (42d1f75) Fix warning
			
* (23549c5) cpu_set_t opacity; fix GNUmakefile cancel9.pass build after changes
			
* (f27bae5) Fix tests build order; reorder some targets
			
* (9393b8d) Minor reorganisation
			
* (751da57) Use more GNU make features to simplify (?) the makefile


2012-10-02  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* sched.h (cpu_set_t): Redefined.
	* implement.h (_sched_cpu_set_vector_): Created as the private equivalent
	of cpu_set.
	(pthread_thread_t_.cpuset): Type change. 
	* sched_setaffinity.c: Reflect changes to cpu_set_t and _sched_cpu_set_vector_.
	* pthread_setaffinity.c: Likewise.
	* create.c: Likewise.
	* pthread_self.c: Likewise.
	* ptw32_new.c: Likewise.


			



2012-10-01
----------

			
* (256c59f) Remove unneccessary "ARCH ="
			
* (314e1aa) Yet more makefile fixups
			
* (fb76e67) Make realclean remove all generated files
			
* (0acaee6) Comment update re static linking of gcc runtime libs; add ARCH to
  DLL_VER
			
* (93b5f01) Fixes around ARCH
			
* (468954c) Fix broken makefiles
			
* (333a384) More reworking of makefiles
			



2012-09-30
----------

			
* (781ae52) Fix install target for static libs
			
* (be2dea7) Add ability to build 32 or 64 bit with MinGW64; Add targets to build
  individual tests (GNU-only)
			
* (eebcc98) Another warning fix
			
* (bd6e6a8) Fix "too many rules" warnings
			
* (13276cd) Remove builds that are not useful
			



2012-09-29
----------

			
* (c93f477) MSVC2010 projects adjusted to allow pthread.c concatenated source compile (for tighter builds) + corrections to prevent 'empty build unit' errors + added new tests to the monolithic test app.
			



2012-09-28
----------

			
* (e4214c6) "[n]make install" target entries
			
* (e91d2cd) patches around config.h; improved "[n]make install" target


2012-09-28  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread.c: pulls all individual source modules into a single
	translation unit.
	* common.mk: Remove everything related to the non-inlined dll targets.
	This removes all the intermediate .c files that #include other .c files
	except for pthread.c.
	* Makefile: Remove and rename targets; remove or edit variables. All
	of this is to remove the intermediate translation unit aggregation
	source files.
	* GNUmakefile: Likewise.
	* attr.c: Removed.
	* barrier.c: Removed.
	* cancel.c: Removed.
	* condvar.c: Removed.
	* exit.c: Removed.
	* fork.c: Removed.
	* misc.c: Removed.
	* mutex.c: Removed.
	* nonportable.c: Removed.
	* private.c: Removed.
	* rwlock.c: Removed.
	* sched.c: Removed.
	* spin.c: Removed.
	* sync.c: Removed.
	* tsd.c: Removed.

2012-09-28  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile: expand on rudimentary install target; add DEST_LIB_NAME
	variable defaulting to "pthread.lib".
	* GNUmakefile: Add install target similar to Makefile with DEST_LIB_NAME
	defaulting to "libpthread.a".

2012-09-28  Daniel Richard. G <danielg at teragram dot com>

	* all: `#include "config.h"`; renamed HAVE_PTW32_CONFIG_H define in
	build files to HAVE_CONFIG_H since we no longer need a
	uniquely-named symbol for this.
	* Bmakefile: Removed _WIN32_WINNT assignment from build files since
	this is now handled in source.
	* Wmakefile: Likewise.
	* Makefile: Added mkdir invocations to "install" target.
	* common.mk: Elaborated the pthread.$(OBJEXT) dependency list.
	* pthread.h: Removed the `#include "config.h"` bit.


			



2012-09-27
----------

			
* (37ac452) fix segfault due to NULL pointer dereference (caused by using NULL as a linked-list sentinel where PTW32_THREAD_REUSE_EMPTY was expected)
			



2012-09-25
----------

			
* (40847f0) Corrected behaviour.
			



2012-09-24
----------

			
* (8111575) Remove unused function
			
* (2c763d9) New test of fibers
			
* (afedf05) Starting to look at fibers for cancellation.
			



2012-09-23
----------

			
* (72da8ce) Correct file name in comment.
			
* (68c8ccf) Output a little more information during "all-tests"
			
* (467dc2e) Remove reliance on min()
			
* (827cbdf) Implemented semi-opaque cpu_set_t
			
* (54684d2) Make output more informative; To-do notes for version 3


2012-09-23  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* GNUmakefile: Modify "all-tests" to use new targets in tests
	GNUmakefile.
	* Makefile: Similarly.


			



2012-09-22
----------

			
* (5c3e7c6) Omnibus patch from Daniel Richard. G
			
* (29bf29f) Fix signed/unsigned comparison (GCE)
			
* (005c1e0) New make target for GC tests; Fix segfault bug
			
* (e4f2672) Minor changes; minor rewrite for CpuCount()
			
* (4e234e5) Remove unused variable.
			
* (bc61504) Found and fixed a bug while analysing another problem



2012-09-22  Daniel Richard. G <danielg at teragram dot com>

	* GNUmakefile: Reordered the command lines in the "help" target
	to match the ordering of the targets in the makefile, which IMO
	is nicer to the eye; tweaked some of the parentheticals for better
	clarity; delete *.manifest files, in case the user just finished
	doing an MSVC build.
	* Makefile: Use *.static_stamp for the static targets instead of
	*.static; added a note re VC++6 and /EHs vs. /EHa; reordered the
	targets, and added a number of new ones (e.g. VSE-small-static);
	added a note recommending *-inlined and *-small-static to make
	things a little easier for users bewildered by the large number of
	targets; reworked the all-tests[-cflags] targets so that (1) more
	useful targets are built first (the small-static targets make it
	easier to track down compilation errors), (2) *-debug build and
	test targets can be used, (3) less-useful build/test permutations
	are enabled only if EXHAUSTIVE and/or MORE_EXHAUSTIVE is defined,
	and (4) /MDd and /MTd are covered too; "nmake all-tests-cflags
	EXHAUSTIVE=1 MORE_EXHAUSTIVE=1" takes a few hours to run; moved
	some of the VCE targets up, since the pattern in the file was
	already to list VCE targets first, then VSE, then VC; actually
	touch the stamp file in the stamp targets.
	* README.NONPORTABLE: It's "DllMain", not "dllMain".
	* common.mk: Start of an attempt to define dependencies for
	pthread.$(OBJEXT).
	* implement.h: Generalized  PTW32_BROKEN_ERRNO into
	PTW32_USES_SEPARATE_CRT; don't do the autostatic-anchoring thing
	if we're not building the library!
	* pthread.h: Moved the  PTW32_CDECL bit into sched.h. pthread.h
	already #includes sched.h, so the latter is a good place to put
	definitions that need to be shared in common; severely simplified
	the errno declaration for Open Watcom, made it applicable only to
	Open Watcom, and made the comment less ambiguous; updated the long
	comment describing  PTW32_BROK^WPTW32_USES_SEPARATE_CRT; added
	(conditional) declaration of pthread_win32_set_terminate_np(), as
	well as ptw32_terminate_handler (so that eh.h doesn't have to get
	involved).
	* pthread_cond_wait.c: Missed a couple of errno conversions.
	* pthread_mutex_consistent.c: Visual Studio (either 2010 or 2008
	Express, don't recall now) actually errored out due to charset
	issues in this file, so I've replaced non-ASCII characters with
	ASCII approximations.
	* ptw32_threadStart.c: Big rewrite of ptw32_threadStart().
	Everything passes with this, except for GCE (and I can't figure
	out why).
	* sched.h: Moved the  PTW32_CDECL section here (and made it
	idempotent); need to #include <stdlib.h> for size_t (one of the test
	programs #includes sched.h as the very first thing); moved the
	DWORD_PTR definition up, since it groups better with the pid_t
	definition; also need ULONG_PTR, don't need PDWORD_PTR; can't use
	PTW32_CONFIG_MSVC6, because if you only #include sched.h you
	don't get that bit in pthread.h; use a cpp symbol
	 (PTW32_HAVE_DWORD_PTR) to inhibit defining *_PTR if needed. Note
	that this isn't #defined inside the conditional, because there are
	no other instances of these typedefs that need to be disabled, and
	sched.h itself is already protected against multiple inclusion;
	DWORD_PTR can't be size_t, because (on MSVC6) the former is "unsigned
	long" and the latter is "unsigned int" and C++ doesn't see them as
	interchangeable; minor edit to the comment... I don't like saying
	"VC++" without the "Microsoft" qualifier; use  PTW32_CDECL instead of
	a literal __cdecl (this was why I moved the  PTW32_CDECL bit into this
	file).
	* semaphore.h: Put in another idempotentized  PTW32_CDECL bit here;
	use  PTW32_CDECL instead of __cdecl, and fixed indentation of function
	formal parameters.

			



2012-09-21
----------

			
* (439ea8b) Add clean up
			
* (4b73cdf) Reorganise DWORD_PTR definition
			
* (0078897) New or modified tests
			
* (0cef671) Add CPU affinity inheritance
			
* (b19d1c4) Add cpu_set link.
  Move sched_setaffinity links to main section.
			
* (1ef2192) Add and update for CPU affinity operations
			


2012-09-21  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* create.c: Major changes to incorporate CPU affinity inheritance.
	* pthread_self.c: Likewise.
	* ptw32_new.c (cpuset): Initialise new pthread_thread_t element.
	* pthread.h (DWORD_PTR): Conditional definition moved to sched.h.
	* sched.h (DWORD_PTR): As above; other changes.
	* sem_post.c: Fix errno handling and restructure.
	* sem_getvalue.c: Fix return value and restructure.
	





2012-09-20
----------

			
* (45da6d6) Add comment
			
* (17f42f6) Convert cpu_set_t support to macros where possible.
  Rewrite tests.
  Compatibility with older compilers.
			
* (c0f3dbd) New manual page
			
* (599ae3f) Cast and printf format change
			



2012-09-19
----------

			
* (19be258) Sched Affinity tests and library fixes
			



2012-09-18
----------

			
* (c487c43) Fix left-shift overrun
			
* (d664e12) Syntax fixes
			
* (c05b67c) New Linux compatibility routines


2012-09-18  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* sched_setaffinity.c: New API to set process CPU affinity in POSIX
	context; compatibility with Linux.
	* pthread_setaffinity.c: Likewise.
	* implement.h (pthread_t_): Added cpuset element.
	* sched.h: Added new prototypes. 
	* sched.h (cpu_set_t): Support for new process and thread affinity API.
	* pthread.h: Added new prototypes.


			



2012-09-16
----------

			
* (e1115a4) Documentation
			
* (8dac93f) Missed errno change

			
2012-09-16  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* README (Version numbering): Changes back to major.minor.micro.
	* README.NONPORTABLE: Updated description around process/thread
	attach/detach routines.




2012-09-13
----------

			
* (9824856..ece3a24) errno handling.
			



2012-09-12
----------

			
* (8310637) Fixed and updated to reflect most recent release version info.
			



2012-09-09
----------

			
* (8ca9cd4) Rework tests.
			



2012-09-05
----------

			
* (9c3837b) Various minor patches.
			
2012-09-05  Daniel Richard. G <danielg at teragram dot com>

	* implement.h: whitespace adjustment.
	* dll.c: Facilitate  PTW32_STATIC_LIB being defined in a header file.





2012-09-04
----------

			
* (6dadd7e) Remove call to pthread_exit()
			
* (6db52ba) Resolve unused variable warning.
			
* (b4deb7d) Fix tests/cancel2.c
			
* (0d3a1ef) Change VC++ EH flags.

2012-09-04  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile (VCEFLAGS): Changed from /EHsc to /EHs which fixed a problem
	in tests/once3.c which was causing it to hang.

			



2012-09-03
----------

			
* (e551d74) Add VC++ static targets.
			
* (a42a0ea) Debug make targets and updates.


2012-09-03  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* Makefile: Remove descriptive info from help target, just list the
	available targets. Output tends to be poorly formatted and cluttered
	otherwise.
	(VCE-static): Add VC++ static build target.
	(VCE-small-static): Likewise.
	(VCE-small-static-debug): Likewise.
	(VCE-small-static-debug): Likewise.

			



2012-09-02
----------

			
* (8b13563) Rename MCS node lock for clarity.
			
* (38165ca) Rewrite and add some comments.
			
2012-09-02  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* All: correct spelling to 'cancellation'.




2012-08-31
----------

			
* (e5f2f84) Fixing some warnings and errors in some builds.


2012-08-31  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_attr_getschedpolicy.c: Remove pedantic arg check.
	* pthread_getschedparam.c: Likewise.
	* pthread_mutex_timelock.c: Restructure to address unreached final
	return statement.

2012-08-31  Daniel Richard. G <danielg at teragram dot com>

	* implement.h (INLINE): only define if building the inlined make targets. G++
	complained about undefined reference to ptw32_robust_mutex_remove() because it
	appears in separate compilation units for "make GCE".



			



2012-08-30
----------

			
* (4d2eb25) Corrects and additions to text.
			
* (67090e8) remove redundant casts
			
* (89c5ef5) Add casts
			



2012-08-29
----------

			
* (247ea67) Fix casts
			
* (d209de4) Prevent displaying modal error dialog
			
* (56465f9) Remove assert statement that is never reached and return 1
			
* (ec5e5b9) replace static initialization of struct with memset
			
* (1bac207) Removed pointless exit(0) and never-reached comment
			
* (920ae14) Missing inits of robustness mutex attribute
			
* (2b70067) Fix type macros; fix cast
			
* (befde6a) Cast fix.
			


2012-08-29  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* ptw32_MCS_lock.c (ptw32_mcs_flag_wait): Fix cast in first 'if' statement.
	* pthread_mutex_consistent.c (comment): Fix awkward grammar.
	* pthread_mutexattr_init.c: Initialize robustness element.

2012-08-29  Daniel Richard. G <danielg at teragram dot com>

	* implement.h  (PTW32_INTERLOCKED_SIZE): Define as long or LONGLONG.
	 (PTW32_INTERLOCKED_SIZEPTR): Define as long* or LONGLONG*.
	* pthread_attr_getschedpolicy.c (SCHED_MAX): Fix cast.
	* ptw32_mutex_check_need_init.c: Fix static mutexattr_t struct initializations.
	* ptw32_threadStart.c (ExceptionFilter): Add cast.
	* ptw32_throw.c: Add cast.





2012-08-21
----------

			
* (d04279c) fixed dependency in MSVC2012 project
			



2012-08-20
----------

			
* (a0aa8b8) add support for MSVC2012: solution + projects added
			



2012-08-19
----------

			
* (1778a75) New test and fixups
			
* (808e7cb) Add pthread_timedjoin_np routine documentation
			
* (b7471d6) Comment spelling errors
			
* (a58d37d) New non-portable function
			
* (2b79bcb) Fix incorrect PTW32_CONFIG_MSVC8 to 7; extra tab in Makefile
			

2012-08-19  Ross Johnson  <ross at homemail dot com dot au>

	* pthread_join.html(pthread_timedjoin_np): Added.
	* index.html(pthread_timedjoin_np): Added link.

2012-08-18  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_timedjoin_np.c: New non-portable function.
	* common.mk (pthread_timedjoin_np): Add new function.
	* nonportable.c (pthread_timedjoin_np): Likewise.





2012-08-17
----------

			
* (5c0ffaa) minimal modification to the MSVC2010 project files: include ;%(DisableSpecificWarnings)
			
* (cb6ef7f) Sub new macros.
			
* (2a299cf) Back out change.
			



2012-08-16
----------

			
* (3345a7a) New simplified macros.
			
2012-08-16  Daniel Richard. G <danielg at teragram dot com>

	* pthread.h  (PTW32_CONFIG_MINGW): Defined to simplify complex macro combination.
	*  (PTW32_CONFIG_MSVC6): Likewise.
	*  (PTW32_CONFIG_MSVC8): Likewise.
	* autostatic.c: Substitute new macros.
	* create.c: Likewise.
	* pthread_cond_wait.c: Likewise.
	* pthread_exit.c: Likewise.
	* pthread_once.c: Likewise.
	* pthread_rwlock_timedwrlock.c: Likewise.
	* pthread_rwlock_wrlock.c: Likewise.
	* pthread_win32_attach_detach_np.c: Likewise.
	* ptw32_relmillisecs.c: Likewise.
	* ptw32_threadDestroy.c: Likewise.
	* ptw32_threadStart.c: Likewise.
	* ptw32_throw.c: Likewise.
	* sem_timedwait.c: Likewise.
	* sem_wait.c: Likewise.
	* implement.h: Likewise.
	* sched.h: Likewise.




2012-08-11
----------

			
* (3b4d714) Option to static link libgcc and minor improvements.
			
* (4f04b3d) Ensure autostatic is always linked in, plus other minor cleanups.

			
2012-08-11  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* common.mk (default_target): restore previous behaviour of outputing
	useful help when "make" is run without a target argument.

2012-08-11  Daniel Richard. G <danielg at teragram dot com>

	* autostatic.c (ptw32_autostatic_anchor): new function; other
	changes aimed at de-abstracting functionality.
	* impliment.h (ptw32_autostatic_anchor): dummy reference to
	ensure that autostatic.o is always linked into static applications.
	* GNUmakefile: Various improvements.
	* Makefile: Likewise.




2012-07-20
----------

			
* (61fd047) PTHREAD_CANCELED casts for C++
			
* (4cfa866) Fix interlocked pointer casts for VC++ x64
			
* (c86e8c4) Don't include RESOURCE_OBJS within other *_OBJS in common.mk
			
* (7f68d56) Fix missing forward declaration
			



2012-07-19
----------

			
* (f52d061..1f04d33) Rationalize and fix
			

2012-07-19  Daniel Richard. G <danielg at teragram dot com>

	* common.mk: New; macros common to all build environment makefiles.
	* Bmakefile: Include new common.mk
	* Makefile: Likewise; various fixes; added normal and small objects
	static build.
	* GNUmakefile: Likewise.




2012-06-18
----------

			
* (3bd39ef) MSVC2010 (non-SP1) complained about incompatible compiler settings
			



2012-06-15
----------

			
* (9f35850) MSVC2010: remove custom build step (leftover from the migration from MSVC2008 and not useful any more, given the new bin+obj directory layout.
			



2012-06-07
----------

			
* (e539174) MSVC2010 projects fixed: librarian didn't have its TargetMachine setting set --> lib failure for 64-bit builds
			



2012-06-06
----------

			
* (3ef72b4) updated to v2.9.1 release
			
* (0aa374a) updated gitignore for MSVC2010 projects
			



2012-05-27
----------

			
* (cc6ba2c) Minor build and test fixes.
			



2012-05-26
----------

			
* (b9afb8d) Move recently incorrectly placed comment.
			
* (9f8c38b) Version 2.9.0 last changes.
			



2012-05-18
----------

			
* (06de582) MSVC2010SP1 fix
			



2012-04-07
----------

			
* (17f2ece) MSVC2010 project fix
			



2012-04-04
----------

			
* (3db2d7b) fix type warning for MSVC2008/WIN64 build
			


2012-03-19
----------

2012-03-19  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* implement.h: Fix interlocked pointer casting under VC++ x64.

2012-03-19  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* implement.h (ptw32_spinlock_check_need_init): added missing
	forward declaration.
	


2012-03-18
----------

			
* (7452bc4) callbacks defined as cdecl



2012-03-18  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* create.c (pthread_create): add __cdecl attribute to thread routine
	arg
	* implement.h (pthread_key_t): add __cdecl attribute to destructor
	element
	(ThreadParms): likewise for start element
	* pthread.h (pthread_create): add __cdecl to prototype start arg
	(pthread_once): likewise for init_routine arg
	(pthread_key_create): likewise for destructor arg
	(ptw32_cleanup_push): replace type of routine arg with previously
	defined ptw32_cleanup_callback_t
	* pthread_key_create.c: add __cdecl attribute to destructor arg
	* pthread_once.c: add __cdecl attribute to init_routine arg
	* ptw32_threadStart.c (start): add __cdecl to start variable type


			



2012-03-01
----------

			
* (c8fbc10) fix fatal run-time stack corruption/crash + Win32 API invocation error when compiling pthreads32 lib in Unicode.
			



2011-09-13
----------

			
* (9adf27c) MSVC2010: shut up a couple of nauseating (and much less useful) warnings
			



2011-08-30
----------

			
* (19975c5) updated MSVC project files: removed superfluous 'copy' post-build action
			



2011-08-22
----------

			
* (727c127) added MSVC2010 project files + solution
			
* (274418d) updated/corrected the MSVC2008 project files
			



2011-07-28
----------

			
* (d477dc8) removed superfluous copy operation (post-build action) from the MSVC2008 project
			



2011-07-27
----------

			
* (339f9c4) fixed the pid_t type for Win32/64 so that it is an integral type which can be typecasted to/from an integer value. Also added a few typecasts in the code to remove a couple of compiler warnings related to this issue.
			



2011-07-22
----------

			
* (06f5bb1) fix for using pthread_win32 with other code, which #define's its own pid_t (to something other than 'int', e.g. (for Win32/64 more appropriate) typedef HANDLE pid_t;
			



2011-07-20
----------

			
* (e72c42b) [i_a] fix for apps using pthreads-Win32: when they do not define __CLEANUP_SEH themselves, they're screwed as they'll receive the '__CLEANUP_C' macros which do NOT work when the pthreads library code itself has actually been build with __CLEANUP_SEH, which is the case when building this stuff in MSVC.
  
  Hence this section is made to 'sensibly autodetect' the cleanup mode, when it hasn't been hardwired in the makefiles / project files.
  
  After all, who expects he MUST define one of these __CLEANUP_XXX defines in his own code when using pthreads-Win32, for whatever reason.
			
* (321adcd) added test case sequence2 for proving fix for monolithic bundling of test cases:
  
  the monolithic test case bundle fails when running sequence1 and reuse1 when other tests have been executed in the same process before either of these; the test bundle does not fail in these test cases when these are executed at start of run (you can only do this for one of them) - turns out to be due to the thread reuse logic kicking in and the test code not anticipating that
  	  -->
  introduction of test sequence2.c to showcase the fix for this, including augmentation of pthread_win32_process_attach_np() to prevent crashes.
			
* (8039228) when unlocking an unlocked mutex, pthread_mutex_unlock() should always produce EPERM for any type of mutex -- see test mutex7.c
			
* (7f260fc) corrected a few test cases, which had a few incorrect assert()s due to the previous merge of my old code and bleeding edge base.
			
* (ae46f23) cdecl missing in functions which are passed to pthread_cleanup_push(): fixed -- matches type ptw32_cleanup_callback_t this way.
			
* (ad791b6) removed type cast for function parameter in pthread_cleanup_push() macro: the typecast would silence subtle parameter differences; now the compiler will yap about those differences, even while the warning/error may be a bit odd.
			
* (eeb6097) fix openmp1 test function definition in test wrapper
			
* (a983f2f) preliminary merge-back of my old work on MSVC2005/MSVC2008 and pthreads-Win32 test cases.
  
  Also updated MSVC project files to 2011 bin/ + obj/ layout standard.
			
* (2b5d652) make sure openmp1 test case compiles with MSVC2008: no C99-style variable declarations in the middle of a scope block.
			



2011-07-19
----------

			
* (de711ec..e20da8d) [i_a] import CVS repository into a separate git repo
			


---




2011-07-06  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_cond_wait.c (pragma inline_depth): this is almost redundant
	now nevertheless fixed thei controlling MSC_VER from "< 800" to
	"< 1400" (i.e. any prior to VC++ 8.0).
	* pthread_once.ci (pragma inline_depth): Likewise.
	* pthread_rwlock_timedwrlock.ci (pragma inline_depth): Likewise.
	* pthread_rwlock_wrlock.ci (pragma inline_depth): Likewise.
	* sem_timedwait.ci (pragma inline_depth): Likewise.
	* sem_wait.ci (pragma inline_depth): Likewise.

2011-07-05  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_win32_attach_detach_np.c: Use strncat_s if available
	to removei a compile warning; MingW supports this routine but we
	continue to use strncat anyway there because it is secure if
	given the correct parameters; fix strncat param 3 to avoid
	buffer overrun exploitation potential.

2011-07-03  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_spin_unlock.c (EPERM): Return success if unlocking a lock
	that is not locked, because single CPU machines wrap a
	PTHREAD_MUTEX_NORMAL mutex, which returns success in this case.
	* pthread_win32_attach_detach_np.c (QUSEREX.DLL): Load from an
	absolute path only which must be the Windows System folder.

2011-07-03 Daniel Richard G. <skunk at iskunk dot org>

	* Makefile (_WIN32_WINNT): Removed; duplicate definition in
	implement.h; more cleanup and enhancements.

2011-07-02 Daniel Richard G. <skunk at iskunk dot org>

	* Makefile: Cleanups and implovements.
	* ptw32_MCS_locks.c: Casting fixes.
	* implement.h: Interlocked call and argument casting macro fixes
	to support older and newer build environments.

2011-07-01  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* *.[ch]  (PTW32_INTERLOCKED_*): Redo 23 and 64 bit versions of these
	macros and re-apply in code to undo the incorrect changes from
	2011-06-29; remove some size_t casts which should not be required
	and may be problematic.a
	There are now two sets of macros:
	PTW32_INTERLOCKED_*_LONG which work only on 32 bit integer variables;
	PTW32_INTERLOCKED_*_SIZE which work on size_t integer variables, i.e.
	LONG for 32 bit systems and LONGLONG for 64 bit systems.
	* implement.h (MCS locks): nextFlag and waitFlag are now HANDLE type.
	* ptw32_MCS_locks.c: Likewise.
	* pthread.h (#include <setjmp.h>): Removed.
	* ptw32_throw.c (#include <setjmp.h>): Added.
	* ptw32_threadStart.c (#include <setjmp.h>): Added.
	* implement.h (#include <setjmp.h>): Added.

2011-06-30  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* pthread_once.c: Tighten 'if' statement casting; fix interlocked
	pointer cast for 64 bit compatibility (missed yesterday); remove
	the superfluous static cleanup routine and call the release routine
	directly if popped.
	* create.c (stackSize): Now type size_t.
	* pthread.h (struct ptw32_thread_t_): Rearrange to fix element alignments.

2011-06-29 Daniel Richard G. <skunk at iskunk dot org>

	* ptw32_relmillisecs.c (ftime):
	  _ftime64_s() is only available in MSVC 2005 or later;
	  _ftime64() is available in MinGW or MSVC 2002 or later;
	  _ftime() is always available.
	* pthread.h (long long): Not defined in older MSVC 6.
	* implement.h (long long): Likewise.
	* pthread_getunique_np.c (long long): Likewise.

2011-06-29  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* *.[ch]  (PTW32_INTERLOCKED_*): These macros should now work for
	both 32 and 64 bit builds. The MingW versions are all inlined asm
	while the MSVC versions expand to their Interlocked* or Interlocked*64
	counterparts appropriately. The argument type have also been changed
	to cast to the appropriate value or pointer size for the architecture.

2011-05-29  Ross Johnson <ross dot johnson at homemail dot com dot au>

	* *.[ch] (#ifdef): Extended cleanup to whole project.

2011-05-29 Daniel Richard G. <skunk at iskunk dot org>

	* Makefile (CC): Define  CC to allow use of other compatible
	compilers such as the Intel compilter icl.
	* implement.h (#if): Fix forms like #if HAVE_SOMETHING.
	* pthread.h: Likewise.
	* sched.h: Likewise;  PTW32_LEVEL_* becomes  PTW32_SCHED_LEVEL_*.
	* semaphore.h: Likewise.

2011-05-11  Ross Johnson <ross.johnson at homemail.com.au>

	* ptw32_callUserDestroyRoutines.c (terminate): Altered includes
	to match ptw32_threadStart.c.
	* GNUmakefile (GCE-inlined-debug, DOPT): Fixed.

2011-04-31  Ross Johnson <ross.johnson at homemail.com.au>

	* (robust mutexes): Added this API. The API is not
	mandatory for implementations that don't support PROCESS_SHARED
	mutexes, nevertheless it was considered useful both functionally
	and for source-level compatibility.
	
2011-03-26  Ross Johnson <ross.johnson at homemail.com.au>

	* pthread_getunique_np.c: New non-POSIX interface for compatibility
	with some other implementations; returns a 64 bit sequence number
	that is unique to each thread in the process.
	* pthread.h (pthread_getunique_np): Added.
	* global.c: Add global sequence counter for above.
	* implement.h: Likewise.

2011-03-26  Ross Johnson  <ross at homemail dot com dot au>

	* pthread_nutex_init.html (robust mutexes): Added
	descriptions for newly implemented interface.
	* pthread_mutexattr_init.html (robust mutexes): Likewise.
	* pthread_getsequence_np.html: New.
	* index.html: Updated.

2011-03-25  Ross Johnson <ross.johnson at homemail.com.au>

	* (cancelLock): Convert to an MCS lock and rename to stateLock.
	* (threadLock): Likewise.
	* (keyLock): Likewise.
	* pthread_mutex*.c: First working robust mutexes.

2011-03-11  Ross Johnson <ross.johnson at homemail.com.au>

	* implement.h  (PTW32_INTERLOCKED_*CREMENT macros): increment/decrement
	using ++/-- instead of add/subtract 1.
	* ptw32_MCS_lock.c: Make casts consistent.

2011-03-09  Ross Johnson <ross.johnson at homemail.com.au>

	* implement.h (ptw32_thread_t_): Add process unique sequence number.
	* global.c: Replace global Critical Section objects with MCS
	queue locks.
	* implement.h: Likewise.
	* pthread_cond_destroy.c: Likewise.
	* pthread_cond_init.c: Likewise.
	* pthread_detach.c: Likewise.
	* pthread_join.c: Likewise.
	* pthread_kill.c: Likewise.
	* pthread_mutex_destroy.c: Likewise.
	* pthread_rwlock_destroy.c: Likewise.
	* pthread_spin_destroy.c: Likewise.
	* pthread_timechange_handler_np.c: Likewise.
	* ptw32_cond_check_need_init.c: Likewise.
	* ptw32_mutex_check_need_init.c: Likewise.
	* ptw32_processInitialize.c: Likewise.
	* ptw32_processTerminate.c: Likewise.
	* ptw32_reuse.c: Likewise.
	* ptw32_rwlock_check_need_init.c: Likewise.
	* ptw32_spinlock_check_need_init.c: Likewise.

2011-03-06  Ross Johnson <ross.johnson at homemail.com.au>

	* several (MINGW64): Cast and call fixups for 64 bit compatibility;
	clean build via x86_64-w64-mingw32 cross toolchain on Linux i686
	targeting x86_64 win64.
	* ptw32_threadStart.c (ptw32_threadStart): Routine no longer attempts
	to pass [unexpected C++] exceptions out of scope but ends the thread
	normally setting EINTR as the exit status.
	* ptw32_throw.c: Fix C++ exception throwing warnings; ignore
	informational warning.
	* implement.h: Likewise with the corresponding header definition.

2011-03-04  Ross Johnson <ross.johnson at homemail.com.au>

	* implement.h  (PTW32_INTERLOCKED_*): Mingw32 does not provide
	the __sync_* intrinsics so implemented them here as macro
	assembler routines. MSVS Interlocked* are emmitted as intrinsics
	wherever possible, so we want mingw to match it; Extended to
	include all interlocked routines used by the library; implemented
	x86_64 versions also.
	* ptw32_InterlockedCompareExchange.c: No code remaining here.
	* ptw32_MCS_lock.c: Converted interlocked calls to use new macros.
	* pthread_barrier_wait.c: Likewise.
	* pthread_once.c: Likewise.
	* ptw32_MCS_lock.c (ptw32_mcs_node_substitute): Name changed to
	ptw32_mcs_node_transfer.

2011-02-28  Ross Johnson <ross.johnson at homemail.com.au>

	* ptw32_relmillisecs.c: If possible, use _ftime64_s or _ftime64
	before resorting to _ftime.

2011-02-27  Ross Johnson <ross.johnson at homemail.com.au>

	* sched_setscheduler.c: Ensure the handle is closed after use.
	* sched_getscheduler.c: Likewise.
	* pthread.h: Remove POSIX compatibility macros; don't define
	timespec if already defined.
	* context.h: Changes for 64 bit.
	* pthread_cancel.c: Likewise.
	* pthread_exit.c: Likewise.
	* pthread_spin_destroy.c: Likewise.
	* pthread_timechange_handler_np.c: Likewise.
	* ptw32_MCS_lock.c: Likewise; some of these changes may
	not be compatible with pre Windows 2000 systems; reverse the order of
	the includes.
	* ptw32_threadStart.c: Likewise.
	* ptw32_throw.c: Likewise.

2011-02-13  Ross Johnson <ross.johnson at homemail.com.au>

	* pthread_self: Add comment re returning 'nil' value to
	indicate failure only to win32 threads that call us.
	* pthread_attr_setstackaddr: Fix comments; note this
	function and it's compliment are now removed from SUSv4.

2011-02-12  Ross Johnson <ross.johnson at homemail.com.au>

	README.NONPORTABLE: Record a description of an obvious
	method for nulling/comparing/hashing pthread_t using a
	union; plus and investigation of a change of type for
	pthread_t (to a union) to neutralise any padding bits and
	bytes if they occur in pthread_t (the current pthread_t struct
	does not contain padding AFAIK, but porting the library to a
	future architecture may introduce them). Padding affects
	byte-by-byte copies and compare operations.

2010-11-16  Ross Johnson <ross.johnson at homemail.com.au>

	* ChangeLog: Add this entry ;-)
	Restore entries from 2007 through 2009 that went missing
	at the last update.

2010-06-19  Ross Johnson <ross.johnson at homemail.com.au>

	* ptw32_MCS_lock.c (ptw32_mcs_node_substitute): Fix variable
	names to avoid using C++ keyword ("new").
	* implement.h (ptw32_mcs_node_substitute): Likewise.
	* pthread_barrier_wait.c: Fix signed/unsigned comparison warning.

2010-06-18  Ramiro Polla  <ramiro.polla at gmail.com >

	* autostatic.c: New file; call pthread_win32_process_*()
	libary init/cleanup routines automatically on application start
	when statically linked.
	* pthread.c (autostatic.c): Included.
	* pthread.h (declspec): Remove import/export defines if compiler
	is MINGW.
	* sched.h (declspec): Likewise.
	* semaphore.h (declspec): Likewise.
	* need_errno.h (declspec): Likewise.
	* Makefile (autostatic.obj): Add for small static builds.
	* GNUmakefile (autostatic.o): Likewise.
	* NEWS (Version 2.9.0): Add changes.
	* README.NONPORTABLE (pthread_win32_process_*): Update
	description.

2010-06-15  Ramiro Polla  <ramiro.polla at gmail.com >

	* Makefile: Remove linkage with the winsock library by default.
	* GNUmakefile: Likewise.
	* pthread_getspecific.c: Likewise by removing calls to WSA
	functions.
	* config.h (RETAIN_WSALASTERROR): Can be defined if necessary.

2010-01-26  Ross Johnson <ross.johnson at homemail.com.au>

	* ptw32_MCS_lock.c (ptw32_mcs_node_substitute): New routine
	to allow relocating the lock owners thread-local node to somewhere
	else, e.g. to global space so that another thread can release the
	lock. Used in pthread_barrier_wait.
	(ptw32_mcs_lock_try_acquire): New routine.
	* pthread_barrier_init: Only one semaphore is used now.
	* pthread_barrier_wait: Added an MCS guard lock with the last thread
	to leave the barrier releasing the lock. This removes a deadlock bug
	observed when there are greater than barrier-count threads
	attempting to cross.
	* pthread_barrier_destroy: Added an MCS guard lock.
        
2009-03-03  Stephan O'Farrill <stephan dot ofarrill at gmail dot com>

	* pthread_attr_getschedpolicy.c: Add "const" to function parameter
	in accordance with SUSv3 (POSIX).
	* pthread_attr_getinheritsched.c: Likewise.
	* pthread_mutexattr_gettype.c: Likewise.

2008-06-30  Ross Johnson  <ross at callisto.canberra.edu.au>

	* pthread_setschedparam.html: Fix "see also" links.

2008-06-06  Robert Kindred  <RKindred at SwRI dot edu>

	* ptw32_throw.c (ptw32_throw): Remove possible reference to NULL
	pointer. (At the same time made the switch block conditionally
	included only if exitCode is needed - RPJ.)
	* pthread_testcancel.c (pthread_testcancel): Remove duplicate and
	misplaced pthread_mutex_unlock().

2008-02-21  Sebastian Gottschalk  <seppig_relay at gmx dot de>

	* pthread_attr_getdetachstate.c (pthread_attr_getdetachstate):
	Remove potential and superfluous null pointer assignment.

2007-11-22  Ivan Pizhenko  <ivanp4 at ua dot fm>

	* pthread.h (gmtime_r): gmtime returns 0 if tm represents a time
	prior to 1/1/1970. Notice this to prevent raising an exception.
	* pthread.h (localtime_r): Likewise for localtime.

2007-07-14  Marcel Ruff  <mr at marcelruff dot info>

	* errno.c (_errno): Fix test for pthread_self() success.
	* need_errno.h: Remove unintentional line wrap from #if line.

2007-07-14  Mike Romanchuk  <mromanchuk at empirix dot com>

	* pthread.h (timespec): Fix tv_sec type.

2007-01-07  Sinan Kaya <sinan.kaya at siemens dot com>

	* need_errno.h: Fix declaration of _errno - the local version of
	_errno() is used, e.g. by WinCE.

2007-01-06  Ross Johnson <ross.johnson at homemail dot com dot au>

	* ptw32_semwait.c: Add check for invalid sem_t after acquiring the
	sem_t state guard mutex and before affecting changes to sema state.
                
2007-01-06  Marcel Ruff <mr at marcelruff dot info>

	* error.c: Fix reference to pthread handle exitStatus member for
	builds that use NEED_ERRNO (i.e. WINCE).
	* context.h: Add support for ARM processor (WinCE).
	* mutex.c (process.h): Exclude for WINCE.
	* create.c: Likewise.
	* exit.c: Likewise.
	* implement.h: Likewise.
	* pthread_detach.c (signal.h): Exclude for WINCE.
	* pthread_join.c: Likewise.
	* pthread_kill.c: Likewise.
	* pthread_rwlock_init.c (errno.h): Remove - included by pthread.h.
	* pthread_rwlock_destroy.c: Likewise.
	* pthread_rwlock_rdlock.c: Likewise.
	* pthread_rwlock_timedrdlock.c: Likewise.
	* pthread_rwlock_timedwrlock.c: Likewise.
	* pthread_rwlock_tryrdlock.c: Likewise.
	* pthread_rwlock_trywrlock.c: likewise.
	* pthread_rwlock_unlock.c: Likewise.
	* pthread_rwlock_wrlock.c: Likewise.
	* pthread_rwlockattr_destroy.c: Likewise.
	* pthread_rwlockattr_getpshared.c: Likewise.
	* pthread_rwlockattr_init.c: Likewise.
	* pthread_rwlockattr_setpshared.c: Likewise.

2007-01-06  Romano Paolo Tenca <rotenca at telvia dot it>

	* pthread_cond_destroy.c: Replace sem_wait() with non-cancelable
	ptw32_semwait() since pthread_cond_destroy() is not a cancellation
	point.
	* implement.h (ptw32_spinlock_check_need_init): Add prototype.
	* ptw32_MCS_lock.c: Reverse order of includes.

2007-01-06  Eric Berge <eric dot berge at quantum dot com>

	* pthread_cond_destroy.c: Add LeaveCriticalSection before returning
	after errors.

2007-01-04  Ross Johnson <ross.johnson at homemail dot com dot au>

	* ptw32_InterlockedCompareExchange.c: Conditionally skip for
	Win64 as not required.
	* pthread_win32_attach_detach_np.c (pthread_win32_process_attach_np):
	Test for InterlockedCompareExchange is not required for Win64.
	* context.h: New file. Included by pthread_cancel.h and any tests
	that need it (e.g. context1.c).
	* pthread_cancel.c: Architecture-dependent context macros moved
	to context.h.

2007-01-04  Kip Streithorst <KSTREITH at ball dot com>

	* implement.h  (PTW32_INTERLOCKED_COMPARE_EXCHANGE): Add Win64
	support.

2006-12-20  Ross Johnson <ross.johnson at homemail.com.au>

	* sem_destroy.c: Fix the race involving invalidation of the sema;
	fix incorrect return of EBUSY resulting from the mutex trylock
	on the private mutex guard.
	* sem_wait.c: Add check for invalid sem_t after acquiring the
	sem_t state guard mutex and before affecting changes to sema state.
	* sem_trywait.c: Likewise.
	* sem_timedwait.c: Likewise.
	* sem_getvalue.c: Likewise.
	* sem_post.c: Similar.
	* sem_post_multiple.c: Likewise.
	* sem_init.c: Set max Win32 semaphore count to SEM_VALUE_MAX (was
	_POSIX_SEM_VALUE_MAX, which is a lower value - the minimum).

	* pthread_win32_attach_detach_np.c (pthread_win32_process_attach_np):
	Load COREDLL.DLL under WINCE to check existence of
	InterlockedCompareExchange() routine. This used to be done to test
	for TryEnterCriticalSection() but was removed when this was no
	longer needed.

2006-01-25  Prashant Thakre <prashant.thakre at gmail.com>

	* pthread_cancel.c: Added _M_IA64 register context support.

2005-05-13  Ross Johnson  <ross at callisto.canberra.edu.au>

	* pthread_kill.c (pthread_kill): Remove check for Win32 thread
	priority (to confirm HANDLE validity). Useless since thread HANDLEs
	a not recycle-unique.

2005-05-30  Vladimir Kliatchko  <vladimir at kliatchko.com>

	* pthread_once.c: Re-implement using an MCS queue-based lock. The form
	of pthread_once is as proposed by Alexander Terekhov (see entry of
	2005-03-13). The MCS lock implementation does not require a unique
	'name' to identify the lock between threads. Attempts to get the Event
	or Semaphore based versions of pthread_once to a satisfactory level
	of robustness have thus far failed. The last problem (avoiding races
	involving non recycle-unique Win32 HANDLEs) was giving everyone
	grey hair trying to solve it.

	* ptw32_MCS_lock.c: New MCS queue-based lock implementation. These
	locks are efficient: they have very low overhead in the uncontended case;
	are efficient in contention and minimise cache-coherence updates in
	managing the user level FIFO queue; do not require an ABI change in the
	library.

2005-05-27  Alexander Gottwald <alexander.gottwald at s1999.tu-chemnitz.de>

	* pthread.h: Some things, like HANDLE, were only defined if
	PTW32_LEVEL was >= 3. They should always be defined.

2005-05-25  Vladimir Kliatchko  <vladimir at kliatchko.com>

	* pthread_once.c: Eliminate all priority operations and other
	complexity by replacing the event with a semaphore. The advantage
	of the change is the ability to release just one waiter if the
	init_routine thread is cancelled yet still release all waiters when
	done. Simplify once_control state checks to improve efficiency
	further.

2005-05-24  Mikael Magnusson  <mikaelmagnusson at glocalnet.net>

	* GNUmakefile: Patched to allow cross-compile with mingw32 on Linux.
	It uses macros instead of referencing dlltool, gcc and g++ directly;
	added a call to ranlib. For example the GC static library can be
	built with:
	make CC=i586-mingw32msvc-gcc RC=i586-mingw32msvc-windres \
	RANLIB=i586-mingw32msvc-ranlib clean GC-static

2005-05-13  Ross Johnson  <ross at callisto.canberra.edu.au>

	* pthread_win32_attach_detach_np.c (pthread_win32_thread_detach_np):
	Move on-exit-only stuff from ptw32_threadDestroy() to here.
	* ptw32_threadDestroy.c: It's purpose is now only to reclaim thread
	resources for detached threads, or via pthread_join() or
	pthread_detach() on joinable threads.
	* ptw32_threadStart.c: Calling user destruct routines has moved to
	pthread_win32_thread_detach_np(); call pthread_win32_thread_detach_np()
	directly if statically linking, otherwise do so via dllMain; store
	thread return value in thread struct for all cases, including
	cancellation and exception exits; thread abnormal exits	go via
	pthread_win32_thread_detach_np.
	* pthread_join.c (pthread_join): Don't try to get return code from
	Win32 thread - always get it from he thread struct.
	* pthread_detach.c (pthread_detach): reduce extent of the thread
	existence check since we now don't care if the Win32 thread HANDLE has
	been closed; reclaim thread resources if the thread has exited already.
	* ptw32_throw.c (ptw32_throw): For Win32 threads that are not implicit,
	only Call thread cleanup if statically linking, otherwise leave it to
	dllMain.
	* sem_post.c (_POSIX_SEM_VALUE_MAX): Change to SEM_VALUE_MAX.
	* sem_post_multiple.c: Likewise.
	* sem_init.c: Likewise.

2005-05-10  Ross Johnson  <ross at callisto.canberra.edu.au>

	* pthread_join.c (pthread_join): Add missing check for thread ID
	reference count in thread existence test; reduce extent of the
	existence test since we don't care if the Win32 thread HANDLE has
	been closed.

2005-05-09  Ross Johnson  <ross at callisto.canberra.edu.au>

	* ptw32_callUserDestroyRoutines.c: Run destructor process (i.e.
	loop over all keys calling destructors) up to
	PTHREAD_DESTRUCTOR_ITERATIONS times if TSD value isn't NULL yet;
	modify assoc management.
	* pthread_key_delete.c: Modify assoc management.
	* ptw32_tkAssocDestroy.c: Fix error in assoc removal from chains.
	* pthread.h
	(_POSIX_THREAD_DESTRUCTOR_ITERATIONS): Define to value specified by
	POSIX.
	(_POSIX_THREAD_KEYS_MAX): Define to value specified by POSIX.
	(PTHREAD_KEYS_MAX): Redefine [upward] to minimum required by POSIX.
	(SEM_NSEMS_MAX): Define to implementation value.
	(SEM_VALUE_MAX): Define to implementation value.
	(_POSIX_SEM_NSEMS_MAX): Redefine to value specified by POSIX.
	(_POSIX_SEM_VALUE_MAX): Redefine to value specified by POSIX.

2005-05-06  Ross Johnson  <ross at callisto.canberra.edu.au>

	* signal.c (sigwait): Add a cancellation point to this otherwise
	no-op.
	* sem_init.c (sem_init): Check for and return ERANGE error.
	* sem_post.c (sem_post): Likewise.
	* sem_post_multiple.c (sem_post_multiple): Likewise.
	* manual (directory): Added; see ChangeLog inside.

2005-05-06  Ross Johnson  <ross at callisto.canberra.edu.au>

	* PortabilityIssues.html: Was nonPortableIssues.html.
	* index.html: Updated; add table of contents at top.
	* *.html: Add pthreads-win32 header info; add link back to the
	index page 'index.html'.

2005-05-06  Ross Johnson  <ross at callisto.canberra.edu.au>

	* index.html: New.
	* nonPortableIssues.html: New.
	* pthread_attr_init.html: New.
	* pthread_attr_setstackaddr.html: New.
	* pthread_attr_setstacksize.html: New.
	* pthread_barrierattr_init.html: New.
	* pthread_barrierattr_setpshared.html: New.
	* pthread_barrier_init.html: New.
	* pthread_barrier_wait.html: New.
	* pthreadCancelableWait.html: New.
	* pthread_cancel.html: New.
	* pthread_cleanup_push.html: New.
	* pthread_condattr_init.html: New.
	* pthread_condattr_setpshared.html: New.
	* pthread_cond_init.html: New.
	* pthread_create.html: New.
	* pthread_delay_np.html: New.
	* pthread_detach.html: New.
	* pthread_equal.html: New.
	* pthread_exit.html: New.
	* pthread_getw32threadhandle_np.html: New.
	* pthread_join.html: New.
	* pthread_key_create.html: New.
	* pthread_kill.html: New.
	* pthread_mutexattr_init.html: New.
	* pthread_mutexattr_setpshared.html: New.
	* pthread_mutex_init.html: New.
	* pthread_num_processors_np.html: New.
	* pthread_once.html: New.
	* pthread_rwlockattr_init.html: New.
	* pthread_rwlockattr_setpshared.html: New.
	* pthread_rwlock_init.html: New.
	* pthread_rwlock_rdlock.html: New.
	* pthread_rwlock_timedrdlock.html: New.
	* pthread_rwlock_timedwrlock.html: New.
	* pthread_rwlock_unlock.html: New.
	* pthread_rwlock_wrlock.html: New.
	* pthread_self.html: New.
	* pthread_setcancelstate.html: New.
	* pthread_setcanceltype.html: New.
	* pthread_setconcurrency.html: New.
	* pthread_setschedparam.html: New.
	* pthread_spin_init.html: New.
	* pthread_spin_lock.html: New.
	* pthread_spin_unlock.html: New.
	* pthread_timechange_handler_np.html: New.
	* pthread_win32_attach_detach_np.html: New.
	* pthread_win32_test_features_np.html: New.
	* sched_get_priority_max.html: New.
	* sched_getscheduler.html: New.
	* sched_setscheduler.html: New.
	* sched_yield.html: New.
	* sem_init.html: New.

2005-05-02  Ross Johnson  <ross at callisto.canberra.edu.au>

	* implement.h (struct pthread_key_t_): Change threadsLock to keyLock
	so as not to be confused with the per thread lock 'threadlock';
	change all references to it.
	* implement.h (struct ThreadKeyAssoc): Remove lock; add prevKey
	and prevThread pointers; re-implemented all routines that use this
	struct. The effect of this is to save one handle per association,
	which could potentially equal the number of keys multiplied by the
	number of threads, accumulating over time - and to free the
	association memory as soon as it is no longer referenced by either
	the key or the thread. Previously, the handle and memory were
	released only after BOTH key and thread no longer referenced the
	association. That is, often no association resources were released
	until the process itself exited. In addition, at least one race
	condition has been removed - where two threads could attempt to
	release the association resources simultaneously - one via
	ptw32_callUserDestroyRoutines and the other via
	pthread_key_delete.
	- thanks to Richard Hughes at Aculab for discovering the problem.
	* pthread_key_create.c: See above.
	* pthread_key_delete.c: See above.
	* pthread_setspecific.c: See above.
	* ptw32_callUserDestroyRoutines.c: See above.
	* ptw32_tkAssocCreate.c: See above.
	* ptw32_tkAssocDestroy.c: See above.

2005-04-27  Ross Johnson  <ross at callisto.canberra.edu.au>

	* sem_wait.c (ptw32_sem_wait_cleanup): after cancellation re-attempt
	to acquire the semaphore to avoid a race with a late sem_post.
	* sem_timedwait.c: Modify comments.

2005-04-25  Ross Johnson  <ross at callisto.canberra.edu.au>

	* ptw32_relmillisecs.c: New module; converts future abstime to 
	milliseconds relative to 'now'.
	* pthread_mutex_timedlock.c: Use new ptw32_relmillisecs routine in
	place of internal code; remove the NEED_SEM code - this routine is now
	implemented for builds that define NEED_SEM (WinCE etc)
	* sem_timedwait.c: Likewise; after timeout or cancellation,
	re-attempt to acquire the semaphore in case one has been posted since
	the timeout/cancel occurred. Thanks to Stefan Mueller.
	* Makefile: Add ptw32_relmillisecs.c module; remove
	ptw32_{in,de}crease_semaphore.c modules.
	* GNUmakefile: Likewise.
	* Bmakefile: Likewise.

	* sem_init.c: Re-write the NEED_SEM code to be consistent with the
	non-NEED_SEM code, but retaining use of an event in place of the w32 sema
	for w32 systems that don't include semaphores (WinCE);
	the NEED_SEM versions of semaphores has been broken for a long time but is
	now fixed and supports all of the same routines as the non-NEED_SEM case.
	* sem_destroy.c: Likewise.
	* sem_wait.c: Likewise.
	* sem_post.c: Likewise.
	* sem_post_multple.c: Likewise.
	* implement.h: Likewise.
	* sem_timedwait.c: Likewise; this routine is now
	implemented for builds that define NEED_SEM (WinCE etc).
	* sem_trywait.c: Likewise.
	* sem_getvalue.c: Likewise.

	* pthread_once.c: Yet more changes, reverting closer to Gottlob Frege's
	first design, but retaining cancellation, priority boosting, and adding
	preservation of W32 error codes to make pthread_once transparent to
	GetLastError.

2005-04-11  Ross Johnson  <ross at callisto.canberra.edu.au>

	* pthread_once.c (pthread_once): Added priority boosting to
	solve starvation problem after once_routine cancellation.
	See notes in file.

2005-04-06  Kevin Lussier <Kevin at codegreennetworks.com>

	* Makefile: Added debug targets for all versions of the library.

2005-04-01  Ross Johnson  <ross at callisto.canberra.edu.au>

	* GNUmakefile: Add target to build libpthreadGC1.a as a static link
	library.
	* Makefile: Likewise for pthreadGC1.lib.

2005-04-01  Kevin Lussier <Kevin at codegreennetworks.com>

	* sem_timedwait.c (sem_timedwait): Increase size of temp variables to
	avoid int overflows for large timeout values.
	* implement.h (int64_t): Include or define.

2005-03-31   Dimitar Panayotov <develop at mail.bg>^M

	* pthread.h: Fix conditional defines for static linking.
	* sched.h: Liekwise.
	* semaphore.h: Likewise.
	* dll.c  (PTW32_STATIC_LIB): Module is conditionally included
	in the build.

2005-03-16  Ross Johnson  <ross at callisto.canberra.edu.au>^M

	* pthread_setcancelstate.c: Undo the last change.

2005-03-16  Ross Johnson  <ross at callisto.canberra.edu.au>^M

	* pthread_setcancelstate.c: Don't check for an async cancel event
	if the library is using alertable async cancel..

2005-03-14  Ross Johnson  <ross at callisto.canberra.edu.au>

	* pthread_once.c (pthread_once): Downgrade interlocked operations to simple
	memory operations where these are protected by the critical section; edit
	comments.

2005-03-13  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_once.c (pthread_once): Completely redesigned; a change was
	required to the ABI (pthread_once_t_), and resulting in a version
	compatibility index increment.

	NOTES:
	The design (based on pseudo code contributed by Gottlob Frege) avoids
	creating a kernel object if there is no contention. See URL for details:-
	http://sources.redhat.com/ml/pthreads-win32/2005/msg00029.html
	This uses late initialisation similar to the technique already used for
	pthreads-win32 mutexes and semaphores (from Alexander Terekhov).

	The subsequent cancellation cleanup additions (by rpj) could not be implemented
	without sacrificing some of the efficiency in Gottlob's design. In particular,
	although each once_control uses it's own event to block on, a global CS is
	required to manage it - since the event must be either re-usable or
	re-creatable under cancellation. This is not needed in the non-cancelable
	design because it is able to mark the event as closed (forever).

	When uncontested, a CS operation is equivalent to an Interlocked operation
	in speed. So, in the final design with cancelability, an uncontested
	once_control operation involves a minimum of five interlocked operations
	(including the LeaveCS operation).
	
	ALTERNATIVES:
	An alternative design from Alexander Terekhov proposed using a named mutex,
	as sketched below:-

	  if (!once_control) { // May be in TLS
	    named_mutex::guard guard(&once_control2);
	      if (!once_control2) {
	         <init>
	         once_control2 = true;
	      }
	    once_control = true;
	  }
	
	A more detailed description of this can be found here:-
	http://groups.yahoo.com/group/boost/message/15442

	[Although the definition of a suitable PTHREAD_ONCE_INIT precludes use of the
	TLS located flag, this is not critical.]
	
	There are three primary concerns though:-
	1) The [named] mutex is 'created' even in the uncontended case.
	2) A system wide unique name must be generated.
	3) Win32 mutexes are VERY slow even in the uncontended 	case. An uncontested
	Win32 mutex lock operation can be 50 (or more) times slower than an
	uncontested EnterCS operation.

	Ultimately, the named mutex trick is making use of the global locks maintained
	by the kernel.

	* pthread.h (pthread_once_t_): One flag and an event HANDLE added.
	(PTHREAD_ONCE_INIT): Additional values included.

2005-03-08  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_once.c (pthread_once): Redesigned to elliminate potential
	starvation problem.
	- reported by Gottlob Frege  <gottlobfrege at gmail.com>

	* ptw32_threadDestroy.c (ptw32_threadDestroy): Implicit threads were
	not closing their Win32 thread duplicate handle.
	- reported by Dmitrii Semii <bogolt at gmail.com>

2005-01-25  Ralf Kubis  <RKubis at mc.com>

	* Attempted acquisition of recursive mutex was causing waiting
	threads to not be woken when the mutex is released.

	* GNUmakefile (GCE): Generate correct version resource comments.

2005-01-01  Konstantin Voronkov  <beowinkle at yahoo.com>

	* pthread_mutex_lock.c (pthread_mutex_lock): The new atomic exchange
	mutex algorithm is known to allow a thread to steal the lock off
	FIFO waiting threads. The next waiting FIFO thread gets a spurious
	wake-up and must attempt to re-acquire the lock. The woken thread
	was setting itself as the mutex's owner before the re-acquisition.

2004-11-22  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_cond_wait.c (ptw32_cond_wait_cleanup): Undo change
	from 2004-11-02.
	* Makefile (DLL_VER): Added for DLL naming suffix - see README.
	* GNUmakefile (DLL_VER): Likewise.
	* Wmakefile (DLL_VER): Likewise.
	* Bmakefile (DLL_VER): Likewise.
	* pthread.dsw (version.rc): Added to MSVS workspace.

2004-11-20  Boudewijn Dekker  <b.dekker at ellipsis.nl>

	* pthread_getspecific.c (pthread_getspecific): Check for
	invalid (NULL) key argument.

2004-11-19  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* config.h  (PTW32_THREAD_ID_REUSE_INCREMENT): Added to allow
	building the library for either unique thread IDs like Solaris
	or non-unique thread IDs like Linux; allows application developers
	to override the library's default insensitivity to some apps
	that may not be strictly POSIX compliant.
	* version.rc: New resource module to encode version information
	within the DLL.
	* pthread.h: Added  PTW32_VERSION* defines and grouped sections
	required by resource compiler together; bulk of file is skipped
	if RC_INVOKED. Defined some error numbers and other names for
	Borland compiler.

2004-11-02  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_cond_wait.c (ptw32_cond_wait_cleanup): Lock CV mutex at
	start of cleanup handler rather than at the end.
	* implement.h  (PTW32_THREAD_REUSE_EMPTY): Renamed from *_BOTTOM.
	(ptw32_threadReuseBottom): New global variable.
	* global.c (ptw32_threadReuseBottom): Declare new variable.
	* ptw32_reuse.c (ptw32_reuse): Change reuse LIFO stack to LILO queue
	to more evenly distribute use of reusable thread IDs; use renamed
	PTW32_THREAD_REUSE_EMPTY.
	* ptw32_processTerminate.c (ptw2_processTerminate): Use renamed
	PTW32_THREAD_REUSE_EMPTY.

2004-10-31  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* implement.h (PThreadState): Add new state value
	'PThreadStateCancelPending'.
	* pthread_testcancel.c (pthread_testcancel): Use new thread
	'PThreadStateCancelPending' state as short cut to avoid entering
	kernel space via WaitForSingleObject() call. This was obviated
	by user space sema acquisition in sem_wait() and sem_timedwait(),
	which are also cancellation points. A call to pthread_testcancel()
	was required, which introduced a kernel call, effectively nullifying
	any gains made by the user space sem acquisition checks.
	* pthread_cancel.c (pthread_cancel): Set new thread
	'PThreadStateCancelPending' state.

2004-10-29  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* implement.h (pthread_t): Renamed to ptw32_thread_t; struct contains
	all thread state.
	* pthread.h (ptw32_handle_t): New general purpose struct to serve
	as a handle for various reusable object IDs - currently only used
	by pthread_t; contains a pointer to ptw32_thread_t (thread state)
	and a general purpose uint for use as a reuse counter or flags etc.
	(pthread_t): typedef'ed to ptw32_handle_t; the uint is the reuse
	counter that allows the library to maintain unique POSIX thread IDs.
	When the pthread struct reuse stack was introduced, threads would
	often acquire an identical ID to a previously destroyed thread. The
	same was true for the pre-reuse stack library, by virtue of pthread_t
	being the address of the thread struct. The new pthread_t retains
	the reuse stack but provides virtually unique thread IDs.
	* sem_wait.c (ptw32_sem_wait_cleanup): New routine used for
	cancellation cleanup.
	* sem_timedwait.c (ptw32_sem_timedwait_cleanup): Likewise.

2004-10-22  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* sem_init.c (sem_init): Introduce a 'lock' element in order to
	replace the interlocked operations with conventional serialisation.
	This is needed in order to be able to atomically modify the sema
	value and perform Win32 sema release operations. Win32 semaphores are
	used instead of events in order to support efficient multiple posting.
	If the whole modify/release isn't atomic, a race between
	sem_timedwait() and sem_post() could result in a release when there is
	no waiting semaphore, which would cause too many threads to proceed.
	* sem_wait.c (sem_wait): Use new 'lock'element.
	* sem_timedwait.c (sem_timedwait): Likewise.
	* sem_trywait.c (sem_trywait): Likewise.
	* sem_post.c (sem_post): Likewise.
	* sem_post_multiple.c (sem_post_multiple): Likewise.
	* sem_getvalue.c (sem_getvalue): Likewise.
	* ptw32_semwait.c (ptw32_semwait): Likewise.
	* sem_destroy.c (sem_destroy): Likewise; also tightened the conditions
	for semaphore destruction; in particular, a semaphore will not be
	destroyed if it has waiters.
	* sem_timedwait.c (sem_timedwait): Added cancel cleanup handler to
	restore sema value when cancelled.
	* sem_wait.c (sem_wait): Likewise.

2004-10-21  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_mutex_unlock.c (pthread_mutex_unlock): Must use PulseEvent()
	rather than SetEvent() to reset the event if there are no waiters.

2004-10-19  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* sem_init.c (sem_init): New semaphore model based on the same idea
	as mutexes, i.e. user space interlocked check to avoid 
	unnecessarily entering kernel space. Wraps the Win32 semaphore and
	keeps it's own counter. Although the motivation to do this has existed
	for a long time, credit goes to Alexander Terekhov for providing
	the logic. I have deviated slightly from AT's logic to add the waiters
	count, which has made the code more complicated by adding cancellation
	cleanup. This also appears to have broken the VCE (C++ EH) version of
	the library (the same problem as previously reported - see BUGS #2),
	only apparently not fixable using the usual workaround, nor by turning
	all optimisation off. The GCE version works fine, so it is presumed to
	be a bug in MSVC++ 6.0. The cancellation exception is thrown and caught
	correctly, but the cleanup class destructor is never called. The failing
	test is tests\semaphore4.c.
	* sem_wait.c (sem_wait): Implemented user space check model.
	* sem_post.c (sem_post): Likewise.
	* sem_trywait.c (sem_trywait): Likewise.
	* sem_timedwait.c (sem_timedwait): Likewise.
	* sem_post_multiple.c (sem_post_multiple): Likewise.
	* sem_getvalue.c (sem_getvalue): Likewise.
	* ptw32_semwait.c (ptw32_semwait): Likewise.
	* implement.h (sem_t_): Add counter element.

2004-10-15  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* implement.h (pthread_mutex_t_): Use an event in place of
	the POSIX semaphore.
	* pthread_mutex_init.c: Create the event; remove semaphore init.
	* pthread_mutex_destroy.c: Delete the event.
	* pthread_mutex_lock.c: Replace the semaphore wait with the event wait.
	* pthread_mutex_trylock.c: Likewise.
	* pthread_mutex_timedlock.c: Likewise.
	* pthread_mutex_unlock.c: Set the event.
	
2004-10-14  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_mutex_lock.c (pthread_mutex_lock): New algorithm using
	Terekhov's xchg based variation of Drepper's cmpxchg model.
	Theoretically, xchg uses fewer clock cycles than cmpxchg (using IA-32
	as a reference), however, in my opinion bus locking dominates the
	equation on smp systems, so the model with the least number of bus
	lock operations in the execution path should win, which is Terekhov's
	variant. On IA-32 uni-processor systems, it's faster to use the
	CMPXCHG instruction without locking the bus than to use the XCHG
	instruction, which always locks the bus. This makes the two variants
	equal for the non-contended lock (fast lane) execution path on up
	IA-32. Testing shows that the xchg variant is faster on up IA-32 as
	well if the test forces higher lock contention frequency, even though
	kernel calls should be dominating the times (on up IA-32, both
	variants used CMPXCHG instructions and neither locked the bus).
	* pthread_mutex_timedlock.c pthread_mutex_timedlock(): Similarly.
	* pthread_mutex_trylock.c (pthread_mutex_trylock): Similarly.
	* pthread_mutex_unlock.c (pthread_mutex_unlock): Similarly.
	* ptw32_InterlockedCompareExchange.c (ptw32_InterlockExchange): New
	function.
	 (PTW32_INTERLOCKED_EXCHANGE): Sets up macro to use inlined
	ptw32_InterlockedExchange.
	* implement.h  (PTW32_INTERLOCKED_EXCHANGE): Set default to
	InterlockedExchange().
	* Makefile: Building using /Ob2 so that asm sections within inline
	functions are inlined.

2004-10-08  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_mutex_destroy.c (pthread_mutex_destroy): Critical Section
	element is no longer required.
	* pthread_mutex_init.c (pthread_mutex_init): Likewise.
	* pthread_mutex_lock.c (pthread_mutex_lock): New algorithm following
	Drepper's paper at http://people.redhat.com/drepper/futex.pdf, but
	using the existing semaphore in place of the futex described in the
	paper. Idea suggested by Alexander Terekhov - see:
	http://sources.redhat.com/ml/pthreads-win32/2003/msg00108.html
	* pthread_mutex_timedlock.c pthread_mutex_timedlock(): Similarly.
	* pthread_mutex_trylock.c (pthread_mutex_trylock): Similarly.
	* pthread_mutex_unlock.c (pthread_mutex_unlock): Similarly.
	* pthread_barrier_wait.c (pthread_barrier_wait): Use inlined version
	of InterlockedCompareExchange() if possible - determined at
	build-time.
	* pthread_spin_destroy.c pthread_spin_destroy(): Likewise.
	* pthread_spin_lock.c pthread_spin_lock():Likewise.
	* pthread_spin_trylock.c (pthread_spin_trylock):Likewise.
	* pthread_spin_unlock.c (pthread_spin_unlock):Likewise.
	* ptw32_InterlockedCompareExchange.c: Sets up macro for inlined use.
	* implement.h (pthread_mutex_t_): Remove Critical Section element.
	 (PTW32_INTERLOCKED_COMPARE_EXCHANGE): Set to default non-inlined
	version of InterlockedCompareExchange().
	* private.c: Include ptw32_InterlockedCompareExchange.c first for
	inlining.
	* GNUmakefile: Add commandline option to use inlined
	InterlockedCompareExchange().
	* Makefile: Likewise.

2004-09-27  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_mutex_lock.c (pthread_mutex_lock): Separate
	PTHREAD_MUTEX_NORMAL logic since we do not need to keep or check some
	state required by other mutex types; do not check mutex pointer arg
	for validity - leave this to the system since we are only checking
	for NULL pointers. This should improve speed of NORMAL mutexes and
	marginally improve speed of other type.
	* pthread_mutex_trylock.c (pthread_mutex_trylock): Likewise.
	* pthread_mutex_unlock.c (pthread_mutex_unlock): Likewise; also avoid
	entering the critical section for the no-waiters case, with approx.
	30% reduction in lock/unlock overhead for this case.
	* pthread_mutex_timedlock.c (pthread_mutex_timedlock): Likewise; also
	no longer keeps mutex if post-timeout second attempt succeeds - this
	will assist applications that wish to impose strict lock deadlines,
	rather than simply to escape from frozen locks.

2004-09-09  Tristan Savatier  <tristan at mpegtv.com>
	* pthread.h (struct pthread_once_t_): Qualify the 'done' element
	as 'volatile'.
	* pthread_once.c: Concerned about possible race condition,
	specifically on MPU systems re concurrent access to multibyte types.
	[Maintainer's note: the race condition is harmless on SPU systems
	and only a problem on MPU systems if concurrent access results in an
	exception (presumably generated by a hardware interrupt). There are
	other instances of similar harmless race conditions that have not
	been identified as issues.]

2004-09-09  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread.h: Declare additional types as volatile.

2004-08-27  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_barrier_wait.c (pthread_barrier_wait): Remove excessive code
	by substituting the internal non-cancelable version of sem_wait
	(ptw32_semwait).

2004-08-25  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_join.c (pthread_join): Rewrite and re-order the conditional
	tests in an attempt to improve efficiency and remove a race
	condition.

2004-08-23  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* create.c (pthread_create): Don't create a thread if the thread
	id pointer location (first arg) is inaccessible. A memory
	protection fault will result if the thread id arg isn't an accessible
	location. This is consistent with GNU/Linux but different to
	Solaris or MKS (and possibly others), which accept NULL as meaning
	'don't return the created thread's ID'. Applications that run
	using pthreads-win32 will run on all other POSIX threads
	implementations, at least w.r.t. this feature.

	It was decided not to copy the Solaris et al behaviour because,
	although it would have simplified some application porting (but only
	from Solaris to Windows), the feature is not technically necessary,
	and the alternative segfault behaviour helps avoid buggy application
	code.

2004-07-01  Anuj Goyal  <anuj.goyal at gmail.com>

	* builddmc.bat: New; Windows bat file to build the library.
	* config.h (__DMC__): Support for Digital Mars compiler.
	* create.c (__DMC__): Likewise.
	* pthread_exit.c (__DMC__): Likewise.
	* pthread_join.c (__DMC__): Likewise.
	* ptw32_threadDestroy.c (__DMC__): Likewise.
	* ptw32_threadStart.c (__DMC__): Likewise.
	* ptw32_throw.c (__DMC__): Likewise.

2004-06-29  Anuj Goyal  <anuj.goyal at gmail.com>

	* pthread.h (__DMC__): Initial support for Digital Mars compiler.

2004-06-29  Will Bryant  <will.bryant at ecosm.com>

	* README.Borland: New; description of Borland changes.
	* Bmakefile: New makefile for the Borland make utility.
	* ptw32_InterlockedCompareExchange.c:
	Add Borland compatible asm code.

2004-06-26  Jason Bard  <BardJA at Npt.NUWC.Navy.Mil>

	* pthread.h (HAVE_STRUCT_TIMESPEC): If undefined, define it
	to avoid timespec struct redefined errors elsewhere in an
	application.

2004-06-21  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread.h (PTHREAD_RECURSIVE_MUTEX_INITIALIZER): Mutex
	initialiser added for compatibility with Linux threads and
	others; currently not included in SUSV3.
	* pthread.h (PTHREAD_ERRORCHECK_MUTEX_INITIALIZER): Likewise.
	* pthread.h (PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP): Likewise.
	* pthread.h (PTHREAD_ERRORCHECK_MUTEX_INITIALIZER_NP): Likewise.

	* ptw32_mutex_check_need_init.c (ptw32_mutex_check_need_init): 
	Add new initialisers.

	* pthread_mutex_lock.c (pthread_mutex_lock): Check for new
	initialisers.
	* pthread_mutex_trylock.c (pthread_mutex_trylock): Likewise.
	* pthread_mutex_timedlock.c (pthread_mutex_timedlock): Likewise.
	* pthread_mutex_unlock.c (pthread_mutex_unlock): Likewise.
	* pthread_mutex_destroy.c (pthread_mutex_destroy): Likewise.

2004-05-20  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* README.NONPORTABLE: Document pthread_win32_test_features_np().
	* FAQ: Update various answers.

2004-05-19  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* Makefile: Don't define _WIN32_WINNT on compiler command line.
	* GNUmakefile: Likewise.

2004-05-16  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_cancel.c (pthread_cancel): Adapted to use auto-detected
	QueueUserAPCEx features at run-time.
	(ptw32_Registercancellation): Drop in replacement for QueueUserAPCEx()
	if it can't be used. Provides older style non-preemptive async
	cancellation.
	* pthread_win32_attach_detach_np.c (pthread_win32_attach_np):
	Auto-detect quserex.dll and the availability of alertdrv.sys;
	initialise and close on process attach/detach.
	* global.c (ptw32_register_cancellation): Pointer to either
	QueueUserAPCEx() or ptw32_Registercancellation() depending on
	availability. QueueUserAPCEx makes pre-emptive async cancellation
	possible.
	* implement.h: Add definitions and prototypes related to QueueUserAPC.

2004-05-16  Panagiotis E. Hadjidoukas <peh at hpclab.ceid.upatras.gr>

	* QueueUserAPCEx (separate contributed package): Provides preemptive
	APC feature.
	* pthread_cancel.c (pthread_cancel): Initial integration of
	QueueUserAPCEx into pthreads-win32 to provide true pre-emptive
	async cancellation of threads, including blocked threads.

2004-05-06  Makoto Kato  <raven at oldskool.jp>

	* pthread.h (DWORD_PTR): Define typedef for older MSVC.
	* pthread_cancel.c (AMD64): Add architecture specific Context register.
	* ptw32_getprocessors.c: Use correct types (DWORD_PTR) for mask
	variables.

2004-04-06  P. van Bruggen  <pietvb at newbridges.nl>

	* ptw32_threadDestroy.c: Destroy threadLock mutex to
	close a memory leak.

2004-02-13  Gustav Hallberg  <gustav at virtutech.com>

	* pthread_equal.c: Remove redundant equality logic.

2003-12-10  Philippe Di Cristo  <philipped at voicebox.com>

	* sem_timedwait.c (sem_timedwait): Fix timeout calculations.

2003-10-20  Alexander Terekhov  <TEREKHOV at de.ibm.com>

	* pthread_mutex_timedlock.c (ptw32_semwait): Move to individual module.
	* ptw32_semwait.c: New module.
	* pthread_cond_wait.c (ptw32_cond_wait_cleanup): Replace cancelable
	sem_wait() call with non-cancelable ptw32_semwait() call.
	* pthread.c (private.c): Re-order for inlining. GNU C warned that
	function ptw32_semwait() was defined 'inline' after it was called.
	* pthread_cond_signal.c (ptw32_cond_unblock): Likewise.
	* pthread_delay_np.c: Disable Watcom warning with comment.
	* *.c (process.h): Remove include from .c files. This is conditionally
	included by the common project include files.

2003-10-20  James Ewing  <james.ewing at sveasoft.com>

	* ptw32_getprocessors.c: Some Win32 environments don't have
	GetProcessAffinityMask(), so always return CPU count = 1 for them.
	* config.h (NEED_PROCESSOR_AFFINITY_MASK): Define for WinCE.
	
2003-10-15  Ross Johnson  <ross at callisto.canberra.edu.au>

	* Re-indented all .c files using default GNU style to remove assorted
	editor ugliness (used GNU indent utility in default style).

2003-10-15  Alex Blanco  <Alex.Blanco at motorola.com>

	* sem_init.c (sem_init): Would call CreateSemaphore even if the sema
	struct calloc failed; was not freeing calloced memory if either
	CreateSemaphore or CreateEvent failed.

2003-10-14  Ross Johnson  <ross at callisto.canberra.edu.au>

	* pthread.h: Add Watcom compiler compatibility. Esssentially just add
	the cdecl attribute to all exposed function prototypes so that Watcom
	generates function call code compatible with non-Watcom built libraries.
	By default, Watcom uses registers to pass function args if possible rather
	than pushing to stack.
	* semaphore.h: Likewise.
	* sched.h: Likewise.
	* pthread_cond_wait.c (ptw32_cond_wait_cleanup): Define with cdecl attribute
	for Watcom compatibility. This routine is called via pthread_cleanup_push so
	it had to match function arg definition.
	* Wmakefile: New makefile for Watcom builds.

2003-09-14  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_setschedparam.c (pthread_setschedparam): Attempt to map
	all priority levels between max and min (as returned by
	sched_get_priority_min/max) to reasonable Win32 priority levels - i.e.
	levels between THREAD_PRIORITY_LOWEST/IDLE to THREAD_PRIORITY_LOWEST and
	between THREAD_PRIORITY_HIGHEST/TIME_CRITICAL to THREAD_PRIORITY_HIGHEST
	while others remain unchanged; record specified thread priority level
	for return by pthread_getschedparam.

	Note that, previously, specified levels not matching Win32 priority levels
	would silently leave the current thread priority unaltered.

	* pthread_getschedparam.c (pthread_getschedparam): Return the priority
	level specified by the latest pthread_setschedparam or pthread_create rather
	than the actual running thread priority as returned by GetThreadPriority - as
	required by POSIX. I.e. temporary or adjusted actual priority levels are not
	returned by this routine.

	* pthread_create.c (pthread_create): For priority levels specified via
	pthread attributes, attempt to map all priority levels between max and
	min (as returned by sched_get_priority_min/max) to reasonable Win32
	priority levels; record priority level given via attributes, or
	inherited from parent thread, for later return by pthread_getschedparam.

	* ptw32_new.c (ptw32_new): Initialise pthread_t_ sched_priority element.

	* pthread_self.c (pthread_self): Set newly created implicit POSIX thread
	sched_priority to Win32 thread's current actual priority. Temporarily
	altered priorities can't be avoided in this case.

	* implement.h (struct pthread_t_): Add new sched_priority element.

2003-09-12  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* sched_get_priority_min.c (sched_get_priority_min): On error should return -1
	with errno set.
	* sched_get_priority_max.c (sched_get_priority_max): Likewise.

2003-09-03  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* w32_cancelableWait.c (ptw32_cancelable_wait): Allow cancellation
	of implicit POSIX threads as well.

2003-09-02  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_win32_attach_detach_np.c (pthread_win32_thread_detach_np):
	Add comment.

	* pthread_exit.c (pthread_exit): Fix to recycle the POSIX thread handle in
	addition to calling user TSD destructors. Move the implicit POSIX thread exit
	handling to ptw32_throw to centralise the logic.

	* ptw32_throw.c (ptw32_throw): Implicit POSIX threads have no point
	to jump or throw to, so cleanup and exit the thread here in this case. For
	processes using the C runtime, the exit code will be set to the POSIX
	reason for the throw (i.e. PTHREAD_CANCEL or the value given to pthread_exit).
	Note that pthread_exit() already had similar logic, which has been moved to
	here.

	* ptw32_threadDestroy.c (ptw32_threadDestroy): Don't close the Win32 handle
	of implicit POSIX threads - expect this to be done by Win32?

2003-09-01  Ross Johnson  <rpj at callisto.canberra.edu.au>

	* pthread_self.c (pthread_self): The newly aquired pthread_t must be
	assigned to the reuse stack, not freed, if the routine fails somehow.

2003-08-13  Ross Johnson  <rpj at ise.canberra.edu.au>

	* pthread_getschedparam.c (pthread_getschedparam): An invalid thread ID
	parameter was returning an incorrect error value; now uses a more exhaustive
	check for validity.

	* pthread_setschedparam.c (pthread_setschedparam): Likewise.

	* pthread_join.c (pthread_join): Now uses a more exhaustive
	check for validity.

	* pthread_detach.c (pthread_detach): Likewise.

	* pthread_cancel.c (pthread_cancel): Likewise.

	* ptw32_threadDestroy.c (ptw32_threadDestroy): pthread_t structs are
	never freed - push them onto a stack for reuse.

	* ptw32_new.c (ptw32_new): Check for reusable pthread_t before dynamically
	allocating new memory for the struct.

	* pthread_kill.c (pthread_kill): New file; new routine; takes only a zero
	signal arg so that applications can check the thread arg for validity; checks
	that the underlying Win32 thread HANDLE is valid.

	* pthread.h (pthread_kill): Add prototype.

	* ptw32_reuse.c (ptw32_threadReusePop): New file; new routine; pop a
	pthread_t off the reuse stack. pthread_t_ structs that have been destroyed, i.e.
	have exited detached or have been joined, are cleaned up and put onto a reuse
	stack. Consequently, thread IDs are no longer freed once calloced. The library
	will attempt to get a struct off this stack before asking the system to alloc
	new memory when creating threads. The stack is guarded by a global mutex.
	(ptw32_threadReusePush): New routine; push a pthread_t onto the reuse stack.

	* implement.h (ptw32_threadReusePush): Add new prototype.
	(ptw32_threadReusePop): Likewise.
	(pthread_t): Add new element.

	* ptw32_processTerminate.c (ptw32_processTerminate): Delete the thread
	reuse lock; free all thread ID structs on the thread reuse stack.

	* ptw32_processInitialize.c (ptw32_processInitialize): Initialise the
	thread reuse lock.

2003-07-19  Ross Johnson  <rpj at ise.canberra.edu.au>

	* GNUmakefile: modified to work under MsysDTK environment.
	* pthread_spin_lock.c (pthread_spin_lock): Check for NULL arg.
	* pthread_spin_unlock.c (pthread_spin_unlock): Likewise.
	* pthread_spin_trylock.c (pthread_spin_trylock): Likewise;
	fix incorrect pointer value if lock is dynamically initialised by
	this function.
	* sem_init.c (sem_init): Initialise sem_t value to quell compiler warning.
	* sem_destroy.c (sem_destroy): Likewise.
	* ptw32_threadStart.c (non-MSVC code sections): Include <exception> rather
	than old-style <new.h>; fix all std:: namespace entities such as
	std::terminate_handler instances and associated methods.
	* ptw32_callUserDestroyRoutines.c (non-MSVC code sections): Likewise.

2003-06-24  Piet van Bruggen  <pietvb at newbridges.nl>

	* pthread_spin_destroy.c (pthread_spin_destroy): Was not freeing the
	spinlock struct.

2003-06-22  Nicolas Barry  <boozai at yahoo.com>

	* pthread_mutex_destroy.c (pthread_mutex_destroy): When called
	with a recursive mutex that was locked by the current thread, the
	function was failing with a success return code.

2003-05-15  Steven Reddie  <Steven.Reddie at ca.com>

	* pthread_win32_attach_detach_np.c (pthread_win32_process_detach_np):
	NULLify ptw32_selfThreadKey after the thread is destroyed, otherwise
	destructors calling pthreads routines might resurrect it again, creating
	memory leaks. Call the underlying Win32 Tls routine directly rather than
	pthread_setspecific().
	(pthread_win32_thread_detach_np): Likewise.

2003-05-14  Viv  <vcotirlea at hotmail.com>

	* pthread.dsp: Change /MT compile flag to /MD.

2003-03-04  Alexander Terekhov  <TEREKHOV at de.ibm.com>

	* pthread_mutex_timedlock.c (pthread_mutex_timedlock): Fix failure to
	set ownership of mutex on second grab after abstime timeout.
	- bug reported by Robert Strycek <strycek at posam.sk>

2002-12-17  Thomas Pfaff  <tpfaff at gmx.net>

	* pthread_mutex_lock.c (ptw32_semwait): New static routine to provide
	a non-cancelable sem_wait() function. This is consistent with the
	way that pthread_mutex_timedlock.c does it.
	(pthread_mutex_lock): Use ptw32_semwait() instead of sem_wait().

2002-12-11  Thomas Pfaff  <tpfaff at gmx.net>

	* pthread_mutex_trylock.c: Should return EBUSY rather than EDEADLK.
	* pthread_mutex_destroy.c: Remove redundant ownership test (the
	trylock call does this for us); do not destroy a recursively locked
	mutex.

2002-09-20  Michael Johnson  <michaelj at maine.rr.com>

	* pthread_cond_destroy.c (pthread_cond_destroy): 
	When two different threads exist, and one is attempting to
	destroy a condition variable while the other is attempting to
	initialize a condition variable that was created with
	PTHREAD_COND_INITIALIZER, a deadlock can occur. Shrink
	the ptw32_cond_list_lock critical section to fix it.

2002-07-31  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* ptw32_threadStart.c (ptw32_threadStart): Thread cancelLock
	destruction moved to ptw32_threadDestroy().

	* ptw32_threadDestroy.c (ptw32_threadDestroy):  Destroy
	the thread's cancelLock. Moved here from ptw32_threadStart.c
	to cleanup implicit threads as well.

2002-07-30  Alexander Terekhov  <TEREKHOV at de.ibm.com>

	* pthread_cond_wait.c (ptw32_cond_wait_cleanup): 
	Remove code designed to avoid/prevent spurious wakeup
	problems. It is believed that the sem_timedwait() call
	is consuming a CV signal that it shouldn't and this is
	breaking the avoidance logic.

2002-07-30  Ross Johnson  <rpj at ise.canberra.edu.au>

	* sem_timedwait.c (sem_timedwait): Tighten checks for
	unreasonable abstime values - that would result in
	unexpected timeout values.

	* w32_CancelableWait.c (ptw32_cancelable_wait):
	Tighten up return value checking and add comments.


2002-06-08  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* sem_getvalue.c (sem_getvalue): Now returns a value for the
	NEED_SEM version (i.e. earlier versions of WinCE).


2002-06-04  Rob Fanner  <rfanner at stonethree.com>

	* sem_getvalue.c (sem_getvalue): The Johnson M. Hart
	approach didn't work - we are forced to take an
	intrusive approach. We try to decrement the sema
	and then immediately release it again to get the
	value. There is a small probability that this may
	block other threads, but only momentarily.

2002-06-03  Ross Johnson  <rpj at ise.canberra.edu.au>

	* sem_init.c (sem_init): Initialise Win32 semaphores
	to _POSIX_SEM_VALUE_MAX (which this implementation
	defines in pthread.h) so that sem_getvalue() can use
	the trick described in the comments in sem_getvalue().
	* pthread.h (_POSIX_SEM_VALUE_MAX): Defined.
	(_POSIX_SEM_NSEMS_MAX): Defined - not used but may be
	useful for source code portability.

2002-06-03  Rob Fanner  <rfanner at stonethree.com>

	* sem_getvalue.c (sem_getvalue): Did not work on NT.
	Use approach suggested by Johnson M. Hart in his book
	"Win32 System Programming".

2002-02-28  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* errno.c: Compiler directive was incorrectly including code.
	* pthread.h: Conditionally added some #defines from config.h
	needed when not building the library. e.g. NEED_ERRNO, NEED_SEM.
	 (PTW32_DLLPORT): Now only defined if _DLL defined.
	(_errno): Compiler directive was incorrectly including prototype.
	* sched.h: Conditionally added some #defines from config.h
	needed when not building the library.
	* semaphore.h: Replace an instance of NEED_SEM that should
	have been NEED_ERRNO. This change currently has nil effect.

	* GNUmakefile: Correct some recent changes.

	* Makefile: Add rule to generate pre-processor output.

2002-02-23  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* pthread_rwlock_timedrdlock.c: New - untested.
	* pthread_rwlock_timedwrlock.c: New - untested.
	
	* Testsuite passed (except known MSVC++ problems)

	* pthread_cond_destroy.c: Expand the time change
	critical section to solve deadlock problem.

	* pthread.c: Add all remaining C modules.
	* pthread.h: Use dllexport/dllimport attributes on functions
	to avoid using pthread.def.
	* sched.h: Likewise.
	* semaphore.h: Likewise.
	* GNUmakefile: Add new targets for single translation
	unit build to maximise inlining potential; generate
	pthread.def automatically.
	* Makefile: Likewise, but no longer uses pthread.def.

2002-02-20  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* pthread_cond_destroy.c (pthread_cond_destroy):
	Enter the time change critical section earlier.

2002-02-17  Ross Johnson  <rpj at setup1.ise.canberra.edu.au

	* Testsuite passed.

	* pthread_timechange_handler_np.c: New; following
	a suggestion from Alexander Terekhov that CVs should
	be broadcast so that they all re-evaluate their
	condition variables and reset a new timeout if
	required, whenever an application receives a
	WM_TIMECHANGE message. This message indicates that
	the system time has been changed. Therefore, CVs
	waiting for a timeout set as an abs_time will possibly
	not wake up at the expected time. Some applications
	may not be tolerant of this.
	* pthread_cond_init.c: Add CV to linked list.
	* pthread_cond_destroy.c: Remove CV from linked list.
	* global.c (ptw32_cond_list_head): New variable.
	(ptw32_cond_list_tail): New variable.
	(ptw32_cond_list_cs): New critical section.
	* ptw32_processInitialize (ptw32_cond_list_cs): Initialize.
	* ptw32_processTerminate (ptw32_cond_list_cs): Delete.


	* Reduce executable size.
	  -----------------------
	When linking with the static library, only those
	routines actually called, either directly or indirectly
	should be included.

	[Gcc has the -ffunction-segments option to do this but MSVC
	doesn't have this feature as far as I can determine. Other
	compilers are undetermined as well. - rpj]

	* spin.c: Split file into function segments.
	* ptw32_spinlock_check_need_init.c: Separated routine from spin.c.
	* pthread_spin_init.c: Likewise.
	* pthread_spin_destroy.c: Likewise.
	* pthread_spin_lock.c: Likewise.
	* pthread_spin_unlock.c: Likewise.
	* pthread_spin_trylock.c: Likewise.

	* sync.c: Split file into function segments.
	* pthread_detach.c: Separated routine from sync.c.
	* pthread_join.c: Likewise.

	* tsd.c: Split file into function segments.
	* pthread_key_create.c: Separated routine from tsd.c.
	* pthread_key_delete.c: Likewise.
	* pthread_setspecific.c: Likewise.
	* pthread_getspecific.c: Likewise.

	* sched.c: Split file into function segments.
	* pthread_attr_setschedpolicy.c: Separated routine from sched.c.
	* pthread_attr_getschedpolicy.c: Likewise.
	* pthread_attr_setschedparam.c: Likewise.
	* pthread_attr_getschedparam.c: Likewise.
	* pthread_attr_setinheritsched.c: Likewise.
	* pthread_attr_getinheritsched.c: Likewise.
	* pthread_setschedparam.c: Likewise.
	* pthread_getschedparam.c: Likewise.
	* sched_get_priority_max.c: Likewise.
	* sched_get_priority_min.c: Likewise.
	* sched_setscheduler.c: Likewise.
	* sched_getscheduler.c: Likewise.
	* sched_yield.c: Likewise.


2002-02-16  Ross Johnson  <rpj at setup1.ise.canberra.edu.au

	Reduce executable size.
	-----------------------
	When linking with the static library, only those
	routines actually called, either directly or indirectly
	should be included.

	[Gcc has the -ffunction-segments option to do this but MSVC
	doesn't have this feature as far as I can determine. Other
	compilers are undetermined as well. - rpj]

	* mutex.c: Split file into function segments.
	* pthread_mutexattr_destroy.c: Separated routine from mutex.c
	* pthread_mutexattr_getpshared.c: Likewise.
	* pthread_mutexattr_gettype.c: Likewise.
	* pthread_mutexattr_init.c: Likewise.
	* pthread_mutexattr_setpshared.c: Likewise.
	* pthread_mutexattr_settype.c: Likewise.
	* ptw32_mutex_check_need_init.c: Likewise.
	* pthread_mutex_destroy.c: Likewise.
	* pthread_mutex_init.c: Likewise.
	* pthread_mutex_lock.c: Likewise.
	* pthread_mutex_timedlock.c: Likewise.
	* pthread_mutex_trylock.c: Likewise.
	* pthread_mutex_unlock.c: Likewise.
	
	* private.c: Split file into function segments.
	* ptw32_InterlockedCompareExchange.c: Separated routine from private.c
	* ptw32_callUserDestroyRoutines.c: Likewise.
	* ptw32_getprocessors.c: Likewise.
	* ptw32_processInitialize.c: Likewise.
	* ptw32_processTerminate.c: Likewise.
	* ptw32_threadDestroy.c: Likewise.
	* ptw32_threadStart.c: Likewise.
	* ptw32_throw.c: Likewise.
	* ptw32_timespec.c: Likewise.
	* ptw32_tkAssocCreate.c: Likewise.
	* ptw32_tkAssocDestroy.c: Likewise.

	* rwlock.c: Split file into function segments.
	* pthread_rwlockattr_destroy.c: Separated routine from rwlock.c
	* pthread_rwlockattr_getpshared.c: Likewise.
	* pthread_rwlockattr_init.c: Likewise.
	* pthread_rwlockattr_setpshared.c: Likewise.
	* ptw32_rwlock_check_need_init.c: Likewise.
	* pthread_rwlock_destroy.c: Likewise.
	* pthread_rwlock_init.c: Likewise.
	* pthread_rwlock_rdlock.c: Likewise.
	* pthread_rwlock_tryrdlock.c: Likewise.
	* pthread_rwlock_trywrlock.c: Likewise.
	* pthread_rwlock_unlock.c: Likewise.
	* pthread_rwlock_wrlock.c: Likewise.

2002-02-10  Ross Johnson  <rpj at setup1.ise.canberra.edu.au

	Reduce executable size.
	-----------------------
	When linking with the static library, only those
	routines actually called, either directly or indirectly
	should be included.

	[Gcc has the -ffunction-segments option to do this but MSVC
	doesn't have this feature as far as I can determine. Other
	compilers are undetermined as well. - rpj]

	* nonportable.c: Split file into function segments.
	* np_delay.c: Separated routine from nonportable.c
	* np_getw32threadhandle.c: Likewise.
	* np_mutexattr_setkind.c: Likewise.
	* np_mutexattr_getkind.c: Likewise.
	* np_num_processors.c: Likewise.
	* np_win32_attach_detach.c: Likewise.

	* misc.c: Split file into function segments.
	* pthread_equal.c: Separated routine from nonportable.c.
	* pthread_getconcurrency.c: Likewise.
	* pthread_once.c: Likewise.
	* pthread_self.c: Likewise.
	* pthread_setconcurrency.c: Likewise.
	* ptw32_calloc.c: Likewise.
	* ptw32_new.c: Likewise.
	* w32_CancelableWait.c: Likewise.
	
2002-02-09  Ross Johnson  <rpj at setup1.ise.canberra.edu.au

	Reduce executable size.
	-----------------------
	When linking with the static library, only those
	routines actually called, either directly or indirectly
	should be included.

	[Gcc has the -ffunction-segments option to do this but MSVC
	doesn't have this feature as far as I can determine. Other
	compilers are undetermined as well. - rpj]

	* condvar.c: Split file into function segments.
	* pthread_condattr_destroy.c: Separated routine from condvar.c.
	* pthread_condattr_getpshared.c: Likewise.
	* pthread_condattr_init.c: Likewise.
	* pthread_condattr_setpshared.c: Likewise.
	* ptw32_cond_check_need_init.c: Likewise.
	* pthread_cond_destroy.c: Likewise.
	* pthread_cond_init.c: Likewise.
	* pthread_cond_signal.c: Likewise.
	* pthread_cond_wait.c: Likewise.
	
2002-02-07  Alexander Terekhov<TEREKHOV at de.ibm.com>

	* nonportable.c (pthread_delay_np): Make a true
	cancellation point. Deferred cancels will interrupt the
	wait.

2002-02-07  Ross Johnson  <rpj at setup1.ise.canberra.edu.au

	* misc.c (ptw32_new): Add creation of cancelEvent so that
	implicit POSIX threads (Win32 threads with a POSIX face)
	are cancelable; mainly so that pthread_delay_np doesn't fail
	if called from the main thread.
	* create.c (pthread_create): Remove creation of cancelEvent
	from here; now in ptw32_new().

	Reduce executable size.
	-----------------------
	When linking with the static library, only those
	routines actually called, either directly or indirectly
	should be included.

	[Gcc has the -ffunction-segments option to do this but MSVC
	doesn't have this feature as far as I can determine. Other
	compilers are undetermined as well. - rpj]

	* barrier.c: All routines are now in separate compilation units;
	This file is used to congregate the separate modules for
	potential inline optimisation and backward build compatibility.
	* cancel.c: Likewise.
	* pthread_barrierattr_destroy.c: Separated routine from cancel.c.
	* pthread_barrierattr_getpshared.c: Likewise.
	* pthread_barrierattr_init.c: Likewise.
	* pthread_barrierattr_setpshared.c: Likewise.
	* pthread_barrier_destroy.c: Likewise.
	* pthread_barrier_init.c: Likewise.
	* pthread_barrier_wait.c: Likewise.
	* pthread_cancel.c: Likewise.
	* pthread_setcancelstate.c: Likewise.
	* pthread_setcanceltype.c: Likewise.
	* pthread_testcancel.c: Likewise.

2002-02-04  Max Woodbury <mtew at cds.duke.edu>

	Reduced name space pollution.
	-----------------------------
	When the appropriate symbols are defined, the headers
	will restrict the definitions of new names. In particular,
	it must be possible to NOT include the <windows.h>
	header and related definitions with some combination
	of symbol definitions. Secondly, it should be possible
	that additional definitions should be limited to POSIX 
	compliant symbols by the definition of appropriate symbols.

	* pthread.h: POSIX conditionals.
	* sched.h: POSIX conditionals.
	* semaphore.h: POSIX conditionals.

	* semaphore.c: Included <limits.h>.
	(sem_init): Changed magic 0x7FFFFFFFL to INT_MAX.
	(sem_getvalue): Trial version.

	Reduce executable size.
	-----------------------
	When linking with the static library, only those
	routines actually called, either directly or indirectly
	should be included.

	[Gcc has the -ffunction-segments option to do this but MSVC
	doesn't have this feature as far as I can determine. Other
	compilers are undetermined as well. - rpj]

	* semaphore.c: All routines are now in separate compilation units;
	This file is used to congregate the separate modules for
	potential inline optimisation and backward build compatibility.
	* sem_close.c: Separated routine from semaphore.c.
	* ptw32_decrease_semaphore.c: Likewise.
	* sem_destroy.c: Likewise.
	* sem_getvalue.c: Likewise.
	* ptw32_increase_semaphore.c: Likewise.
	* sem_init.c: Likewise.
	* sem_open.c: Likewise.
	* sem_post.c: Likewise.
	* sem_post_multiple.c: Likewise.
	* sem_timedwait.c: Likewise.
	* sem_trywait.c: Likewise.
	* sem_unlink.c: Likewise.
	* sem_wait.c: Likewise.

2002-02-04  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	The following extends the idea above to the rest of pthreads-win32 - rpj
	
	* attr.c: All routines are now in separate compilation units;
	This file is used to congregate the separate modules for
	potential inline optimisation and backward build compatibility.
	* pthread_attr_destroy.c: Separated routine from attr.c.
	* pthread_attr_getdetachstate.c: Likewise.
	* pthread_attr_getscope.c: Likewise.
	* pthread_attr_getstackaddr.c: Likewise.
	* pthread_attr_getstacksize.c: Likewise.
	* pthread_attr_init.c: Likewise.
	* pthread_attr_is_attr.c: Likewise.
	* pthread_attr_setdetachstate.c: Likewise.
	* pthread_attr_setscope.c: Likewise.
	* pthread_attr_setstackaddr.c: Likewise.
	* pthread_attr_setstacksize.c: Likewise.

	* pthread.c: Agregation of agregate modules for super-inlineability.

2002-02-02  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* cancel.c: Rearranged some code and introduced checks
	to disable cancellation at the start of a thread's cancellation
	run to prevent double cancellation. The main problem
	arises if a thread is canceling and then receives a subsequent
	async cancel request.
	* private.c: Likewise.
	* condvar.c: Place pragmas around cleanup_push/pop to turn
	off inline optimisation (/Obn where n>0 - MSVC only). Various
	optimisation switches in MSVC turn this on, which interferes with
	the way that cleanup handlers are run in C++ EH and SEH
	code. Application code compiled with inline optimisation must
	also wrap cleanup_push/pop blocks with the pragmas, e.g.
	  #pragma inline_depth(0)
	  pthread_cleanup_push(...)
	    ...
	  pthread_cleanup_pop(...)
	  #pragma inline_depth(8)
	* rwlock.c: Likewise.
	* mutex.c: Remove attempts to inline some functions.
	* signal.c: Modify misleading comment.

2002-02-01  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* semaphore.c (sem_trywait): Fix missing errno return
	for systems that define NEED_SEM (e.g. early WinCE).
	* mutex.c (pthread_mutex_timedlock): Return ENOTSUP
	for systems that define NEED_SEM since they don't
	have sem_trywait().

2002-01-27  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* mutex.c (pthread_mutex_timedlock): New function suggested by
	Alexander Terekhov. The logic required to implement this
	properly came from Alexander, with some collaboration
	with Thomas Pfaff.
	(pthread_mutex_unlock): Wrap the waiters check and sema
	post in a critical section to prevent a race with
	pthread_mutex_timedlock.
	(ptw32_timed_semwait): New function;
	returns a special result if the absolute timeout parameter
	represents a time already passed when called; used by
	pthread_mutex_timedwait(). Have deliberately not reused
	the name "ptw32_sem_timedwait" because they are not the same
	routine.
	* condvar.c (ptw32_cond_timedwait): Use the new sem_timedwait()
	instead of ptw32_sem_timedwait(), which now has a different
	function. See previous.
	* implement.h: Remove prototype for ptw32_sem_timedwait.
	See next.
	(pthread_mutex_t_): Add critical section element for access
	to lock_idx during mutex post-timeout processing.
	* semaphore.h (sem_timedwait): See next.
	* semaphore.c (sem_timedwait): See next.
	* private.c (ptw32_sem_timedwait): Move to semaphore.c
	and rename as sem_timedwait().

2002-01-18  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* sync.c (pthread_join): Was getting the exit code from the
	calling thread rather than the joined thread if
	defined(__MINGW32__) && !defined(__MSVCRT__).

2002-01-15  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* pthread.h: Unless the build explicitly defines PTW32_CLEANUP_SEH,
	PTW32_CLEANUP_CXX, or PTW32_CLEANUP_C, then the build defaults to
	PTW32_CLEANUP_C style cleanup. This style uses setjmp/longjmp
	in the cancellation and thread exit implementations and therefore
	won't do stack unwinding if linked to applications that have it
	(e.g. C++ apps). This is currently consistent with most/all
	commercial Unix POSIX threads implementations.

	* spin.c (pthread_spin_init): Edit renamed function call.
	* nonportable.c (pthread_num_processors_np): New.
	(pthread_getprocessors_np): Renamed to ptw32_getprocessors
	and moved to private.c.
	* private.c (pthread_getprocessors): Moved here from
	nonportable.c.
	* pthread.def (pthread_getprocessors_np): Removed
	from export list.

	* rwlock.c (pthread_rwlockattr_init): New.
	(pthread_rwlockattr_destroy): New.
	(pthread_rwlockattr_getpshared): New.
	(pthread_rwlockattr_setpshared): New.

2002-01-14  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* attr.c (pthread_attr_setscope): Fix struct pointer
	indirection error introduced 2002-01-04.
	(pthread_attr_getscope): Likewise.

2002-01-12  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* pthread.dsp (SOURCE): Add missing source files.

2002-01-08  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* mutex.c (pthread_mutex_trylock): use
	ptw32_interlocked_compare_exchange function pointer
	rather than ptw32_InterlockedCompareExchange() directly
	to retain portability to non-iX86 processors,
	e.g. WinCE etc. The pointer will point to the native
	OS version of InterlockedCompareExchange() if the
	OS supports it (see ChangeLog entry of 2001-10-17).

2002-01-07  Thomas Pfaff <tpfaff at gmx.net>, Alexander Terekhov <TEREKHOV at de.ibm.com>

	* mutex.c (pthread_mutex_init): Remove critical
	section calls.
	(pthread_mutex_destroy): Likewise.
	(pthread_mutex_unlock): Likewise.
	(pthread_mutex_trylock): Likewise; uses
	ptw32_InterlockedCompareExchange() to avoid need for
	critical section; library is no longer i386 compatible;
	recursive mutexes now increment the lock count rather
	than return EBUSY; errorcheck mutexes return EDEADLCK
	rather than EBUSY. This behaviour is consistent with the
	Solaris pthreads implementation.
	* implement.h (pthread_mutex_t_): Remove critical
	section element - no longer needed.
	

2002-01-04  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* attr.c (pthread_attr_setscope): Add more error
	checking and actually store the scope value even
	though it's not really necessary.
	(pthread_attr_getscope): Return stored value.
	* implement.h (pthread_attr_t_): Add new scope element.
	* ANNOUNCE: Fix out of date comment next to
	pthread_attr_setscope in conformance section.

2001-12-21  Alexander Terekhov <TEREKHOV at de.ibm.com>

	* mutex.c (pthread_mutex_lock): Decrementing lock_idx was
	not thread-safe.
	(pthread_mutex_trylock): Likewise.

2001-10-26  prionx@juno.com

	* semaphore.c (sem_init): Fix typo and missing bracket
	in conditionally compiled code. Only older versions of
	WinCE require this code, hence it doesn't normally get
	tested; somehow when sem_t reverted to an opaque struct
	the calloc NULL check was left in the conditionally included
	section.
	(sem_destroy): Likewise, the calloced sem_t wasn't being freed.

2001-10-25  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* GNUmakefile (libwsock32): Add to linker flags for
	WSAGetLastError() and WSASetLastError().
	* Makefile (wsock32.lib): Likewise.
	* create.c: Minor mostly inert changes.
	* implement.h  (PTW32_MAX): Move into here and renamed
	from sched.h.
	 (PTW32_MIN): Likewise.
	* GNUmakefile (TEST_ICE): Define if testing internal
	implementation of InterlockedCompareExchange.
	* Makefile (TEST_ICE): Likewise.
	* private.c (TEST_ICE): Likewise.
	
2001-10-24  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* attr.c (pthread_attr_setstacksize): Quell warning
	from LCC by conditionally compiling the stacksize
	validity check. LCC correctly warns that the condition
	(stacksize < PTHREAD_STACK_MIN) is suspicious
	because STACK_MIN is 0 and stacksize is of type
	size_t (or unsigned int).

2001-10-17  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* barrier.c: Move _LONG and _LPLONG defines into
	implement.h; rename to  PTW32_INTERLOCKED_LONG and
	PTW32_INTERLOCKED_LPLONG respectively.
	* spin.c: Likewise; ptw32_interlocked_compare_exchange used
	in place of InterlockedCompareExchange directly.
	* global.c (ptw32_interlocked_compare_exchange): Add
	prototype for this new routine pointer to be used when
	InterlockedCompareExchange isn't supported by Windows.
	* nonportable.c (pthread_win32_process_attach_np): Check for
	support of InterlockedCompareExchange in kernel32 and assign its
	address to ptw32_interlocked_compare_exchange if it exists, or
	our own ix86 specific implementation ptw32_InterlockedCompareExchange.
	*private.c (ptw32_InterlockedCompareExchange): An
	implementation of InterlockedCompareExchange() which is
	specific to ix86; written directly in assembler for either
	MSVC or GNU C; needed because Windows 95 doesn't support
	InterlockedCompareExchange().

	* sched.c (sched_get_priority_min): Extend to return
	THREAD_PRIORITY_IDLE.
	(sched_get_priority_max): Extend to return
	THREAD_PRIORITY_CRITICAL.

2001-10-15  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* spin.c (pthread_spin_lock): PTHREAD_SPINLOCK_INITIALIZER
	was causing a program fault.
	(pthread_spin_init): Could have alloced memory
	without freeing under some error conditions.

	* mutex.c (pthread_mutex_init): Move memory
	allocation of mutex struct after checking for
	PROCESS_SHARED.

2001-10-12  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* spin.c (pthread_spin_unlock): Was not returning
	EPERM if the spinlock was not locked, for multi CPU
	machines.

2001-10-08  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* spin.c (pthread_spin_trylock): Was not returning
	EBUSY for multi CPU machines.

2001-08-24  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* condvar.c (pthread_cond_destroy): Remove cv element
	that is no longer used.
	* implement.h: Likewise.

2001-08-23  Alexander Terekhov <TEREKHOV at de.ibm.com>

	* condvar.c (pthread_cond_destroy): fix bug with
	respect to deadlock in the case of concurrent
	_destroy/_unblock; a condition variable can be destroyed
	immediately after all the threads that are blocked on
	it are awakened.

2001-08-23  Phil Frisbie, Jr. <phil at hawksoft.com>

	* tsd.c (pthread_getspecific): Preserve the last
	winsock error [from WSAGetLastError()].

2001-07-18  Scott McCaskill <scott at magruder.org>

	* mutex.c (pthread_mutexattr_init): Return ENOMEM
	immediately and don't dereference the NULL pointer
	if calloc fails.
	(pthread_mutexattr_getpshared): Don't dereference
	a pointer that is possibly NULL.
	* barrier.c (pthread_barrierattr_init): Likewise
	(pthread_barrierattr_getpshared): Don't dereference
	a pointer that is possibly NULL.
	* condvar.c (pthread_condattr_getpshared): Don't dereference
	a pointer that is possibly NULL.

2001-07-15  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* rwlock.c (pthread_rwlock_wrlock): Is allowed to be
	a cancellation point; re-enable deferred cancelability
	around the CV call.

2001-07-10  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* barrier.c: Still more revamping. The exclusive access
	mutex isn't really needed so it has been removed and replaced
	by an InterlockedDecrement(). nSerial has been removed.
	iStep is now dual-purpose. The process shared attribute
	is now stored in the barrier struct.
	* implement.h (pthread_barrier_t_): Lost some/gained one
	elements.
	* private.c (ptw32_threadStart): Removed some comments.

2001-07-10  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* barrier.c: Revamped to fix the race condition. Two alternating
	semaphores are used instead of the PulseEvent. Also improved
	overall throughput by returning PTHREAD_BARRIER_SERIAL_THREAD
	to the first waking thread.
	* implement.h (pthread_barrier_t_): Revamped.

2001-07-09  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* barrier.c: Fix several bugs in all routines. Now passes
	tests/barrier5.c which is fairly rigorous. There is still
	a non-optimal work-around for a race condition between
	the barrier breeched event signal and event wait. Basically
	the last (signalling) thread to hit the barrier yields
	to allow any other threads, which may have lost the race,
	to complete.

2001-07-07  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* barrier.c: Changed synchronisation mechanism to a
	Win32 manual reset Event and use PulseEvent to signal
	waiting threads. If the implementation continued to use
	a semaphore it would require a second semaphore and
	some management to use them alternately as barriers. A
	single semaphore allows threads to cascade from one barrier
	through the next, leaving some threads blocked at the first.
	* implement.h (pthread_barrier_t_): As per above.
	* general: Made a number of other routines inlinable.

2001-07-07  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* spin.c: Revamped and working; included static initialiser.
	Now beta level.
	* barrier.c: Likewise.
	* condvar.c: Macro constant change; inline auto init routine.
	* mutex.c: Likewise.
	* rwlock.c: Likewise.
	* private.c: Add support for spinlock initialiser.
	* global.c: Likewise.
	* implement.h: Likewise.
	* pthread.h (PTHREAD_SPINLOCK_INITIALIZER): Fix typo.

2001-07-05  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* barrier.c: Remove static initialisation - irrelevent
	for this object.
	* pthread.h (PTHREAD_BARRIER_INITIALIZER): Removed.
	* rwlock.c (pthread_rwlock_wrlock): This routine is
	not a cancellation point - disable deferred
	cancellation around call to pthread_cond_wait().

2001-07-05  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* spin.c: New module implementing spin locks.
	* barrier.c: New module implementing barriers.
	* pthread.h (_POSIX_SPIN_LOCKS): defined.
	(_POSIX_BARRIERS): Defined.
	(pthread_spin_*): Defined.
	(pthread_barrier*): Defined.
	(PTHREAD_BARRIER_SERIAL_THREAD): Defined.
	* implement.h (pthread_spinlock_t_): Defined.
	(pthread_barrier_t_): Defined.
	(pthread_barrierattr_t_): Defined.

	* mutex.c (pthread_mutex_lock): Return with the error
	if an auto-initialiser initialisation fails.

	* nonportable.c (pthread_getprocessors_np): New; gets the
	number of available processors for the current process.

2001-07-03  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* pthread.h (_POSIX_READER_WRITER_LOCKS): Define it
	if not already defined.

2001-07-01  Alexander Terekhov <TEREKHOV at de.ibm.com>

	* condvar.c: Fixed lost signal bug reported by Timur Aydin
	(taydin@snet.net).
	[RPJ (me) didn't translate the original algorithm
	correctly.]
	* semaphore.c: Added sem_post_multiple; this is a useful
	routine, but it doesn't appear to be standard. For now it's
	not an exported function.
	
2001-06-25  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* create.c (pthread_create): Add priority inheritance
	attributes.
	* mutex.c (pthread_mutex_lock): Remove some overhead for
	PTHREAD_MUTEX_NORMAL mutex types. Specifically, avoid
	calling pthread_self() and pthread_equal() to check/set
	the mutex owner. Introduce a new pseudo owner for this
	type. Test results suggest increases in speed of up to
	90% for non-blocking locks.
	This is the default type of mutex used internally by other
	synchronising objects, ie. condition variables and
	read-write locks. The test rwlock7.c shows about a
	30-35% speed increase over snapshot 2001-06-06. The
	price of this is that the application developer
	must ensure correct behaviour, or explicitly set the
	mutex to a safer type such as PTHREAD_MUTEX_ERRORCHECK.
	For example, PTHREAD_MUTEX_NORMAL (or PTHREAD_MUTEX_DEFAULT)
	type mutexes will not return an error if a thread which is not
	the owner calls pthread_mutex_unlock. The call will succeed
	in unlocking the mutex if it is currently locked, but a
	subsequent unlock by the true owner will then fail with EPERM.
	This is however consistent with some other implementations.
	(pthread_mutex_unlock): Likewise.
	(pthread_mutex_trylock): Likewise.
	(pthread_mutex_destroy): Likewise.
	* attr.c (pthread_attr_init): PTHREAD_EXPLICIT_SCHED is the
	default inheritance attribute; THREAD_PRIORITY_NORMAL is
	the default priority for new threads.
	* sched.c (pthread_attr_setschedpolicy): Added routine.
	(pthread_attr_getschedpolicy): Added routine.
	(pthread_attr_setinheritsched): Added routine.
	(pthread_attr_getinheritsched): Added routine.
	* pthread.h (sched_rr_set_interval): Added as a macro;
	returns -1 with errno set to ENOSYS.

2001-06-23  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	*sched.c (pthread_attr_setschedparam): Add priority range
	check.
	(sched_setscheduler): New function; checks for a valid
	pid and policy; checks for permission to set information
	in the target process; expects pid to be a Win32 process ID,
	not a process handle; the only scheduler policy allowed is
	SCHED_OTHER.
	(sched_getscheduler): Likewise, but checks for permission
	to query.
	* pthread.h (SCHED_*): Moved to sched.h as defined in the
	POSIX standard.
	* sched.h (SCHED_*): Moved from pthread.h.
	(pid_t): Defined if necessary.
	(sched_setscheduler): Defined.
	(sched_getscheduler): Defined.
	* pthread.def (sched_setscheduler): Exported.
	(sched_getscheduler): Likewise.

2001-06-23  Ralf Brese <Ralf.Brese at pdb4.siemens.de>

	* create.c (pthread_create): Set thread priority from
	thread attributes.

2001-06-18  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* Made organisational-only changes to UWIN additions.
	* dll.c (dllMain): Moved UWIN process attach code
	to pthread_win32_process_attach_np(); moved
	instance of pthread_count to global.c.
	* global.c (pthread_count): Moved from dll.c.
	* nonportable.c (pthread_win32_process_attach_np):
	Moved _UWIN code to here from dll.c.
	* implement.h (pthread_count): Define extern int.
	* create.c (pthread_count): Remove extern int.
	* private.c (pthread_count): Likewise.
	* exit.c (pthread_count): Likewise.

2001-06-18  David Korn <dgk at research.att.com>

	* dll.c: Added changes necessary to work with UWIN.
	* create.c: Likewise.
	* pthread.h: Likewise.
	* misc.c: Likewise.
	* exit.c: Likewise.
	* private.c: Likewise.
	* implement.h: Likewise.
	There is some room at the start of struct pthread_t_
	to implement the signal semantics in UWIN's posix.dll
	although this is not yet complete.
	* Nmakefile: Compatible with UWIN's Nmake utility.
	* Nmakefile.tests: Likewise - for running the tests.

2001-06-08  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* semaphore.h (sem_t): Fixed for compile and test.
	* implement.h (sem_t_): Likewise.
	* semaphore.c: Likewise.
	* private.c (ptw32_sem_timedwait): Updated to use new
	opaque sem_t.

2001-06-06  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* semaphore.h (sem_t): Is now an opaque pointer;
	moved actual definition to implement.h.
	* implement.h (sem_t_): Move here from semaphore.h;
	was the definition of sem_t.
	* semaphore.c: Wherever necessary, changed use of sem
	from that of a pointer to a pointer-pointer; added
	extra checks for a valid sem_t; NULL sem_t when
	it is destroyed; added extra checks when creating
	and destroying sem_t elements in the NEED_SEM
	code branches; changed from using a pthread_mutex_t
	((*sem)->mutex) to CRITICAL_SECTION ((*sem)->sem_lock_cs)
	in NEED_SEM branches for access serialisation.

2001-06-06  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* mutex.c (pthread_mutexattr_init): Remove 
	ptw32_mutex_default_kind.
	
2001-06-05  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* nonportable.c (pthread_mutex_setdefaultkind_np):
	Remove - should not have been included in the first place.
	(pthread_mutex_getdefaultkind_np): Likewise.
	* global.c (ptw32_mutex_default_kind): Likewise.
	* mutex.c (pthread_mutex_init): Remove use of
	ptw32_mutex_default_kind.
	* pthread.h (pthread_mutex_setdefaultkind_np): Likewise.
	(pthread_mutex_getdefaultkind_np): Likewise.
	* pthread.def (pthread_mutexattr_setkind_np): Added.
	(pthread_mutexattr_getkind_np): Likewise.

	* README: Many changes that should have gone in before
	the last snapshot.
	* README.NONPORTABLE: New - referred to by ANNOUNCE
	but never created; documents the non-portable routines
	included in the library - moved from README with new
	routines added.
	* ANNOUNCE (pthread_mutexattr_setkind_np): Added to
	compliance list.
	(pthread_mutexattr_getkind_np): Likewise.

2001-06-04  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* condvar.c: Add original description of the algorithm as
	developed by Terekhov and Thomas, plus reference to
	README.CV.

2001-06-03  Alexander Terekhov <TEREKHOV at de.ibm.com>, Louis Thomas <lthomas at arbitrade.com>

	* condvar.c (pthread_cond_init): Completely revamped.
	(pthread_cond_destroy): Likewise.
	(ptw32_cond_wait_cleanup): Likewise.
	(ptw32_cond_timedwait): Likewise.
	(ptw32_cond_unblock): New general signaling routine.
	(pthread_cond_signal): Now calls ptw32_cond_unblock.
	(pthread_cond_broadcast): Likewise.
	* implement.h (pthread_cond_t_): Revamped.
	* README.CV: New; explanation of the above changes.

2001-05-30  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* pthread.h (rand_r): Fake using _seed argument to quell
	compiler warning (compiler should optimise this away later).

	* GNUmakefile (OPT): Leave symbolic information out of the library
	and increase optimisation level - for smaller faster prebuilt
	dlls.
	
2001-05-29  Milan Gardian <Milan.Gardian at LEIBINGER.com>

	* Makefile: fix typo.
	* pthreads.h: Fix problems with stdcall/cdecl conventions, in particular
	remove the need for PT_STDCALL everywhere; remove warning supression.
	* (errno): Fix the longstanding "inconsistent dll linkage" problem
	with errno; now also works with /MD debugging libs - 
	warnings emerged when compiling pthreads library with /MD (or /MDd)
	compiler switch, instead of /MT (or /MTd) (i.e. when compiling pthreads
	using Multithreaded DLL CRT instead of Multithreaded statically linked
	CRT).
	* create.c (pthread_create): Likewise; fix typo.
	* private.c (ptw32_threadStart): Eliminate use of terminate() which doesn't
	throw exceptions.
	* Remove unnecessary #includes from a number of modules -
	[I had to #include malloc.h in implement.h for gcc - rpj].

2001-05-29  Thomas Pfaff <tpfaff at gmx.net>

	* pthread.h (PTHREAD_MUTEX_DEFAULT): New; equivalent to
	PTHREAD_MUTEX_DEFAULT_NP.
	* (PTHREAD_MUTEX_NORMAL): Similarly.
	* (PTHREAD_MUTEX_ERRORCHECK): Similarly.
	* (PTHREAD_MUTEX_RECURSIVE): Similarly.
	* (pthread_mutex_setdefaultkind_np): New; Linux compatibility stub
	for pthread_mutexattr_settype.
	* (pthread_mutexattr_getkind_np): New; Linux compatibility stub
	for pthread_mutexattr_gettype.
	* mutex.c (pthread_mutexattr_settype): New; allow
	the following types of mutex:
	  PTHREAD_MUTEX_DEFAULT_NP
	  PTHREAD_MUTEX_NORMAL_NP
	  PTHREAD_MUTEX_ERRORCHECK_NP
	  PTHREAD_MUTEX_RECURSIVE_NP
	* Note that PTHREAD_MUTEX_DEFAULT is equivalent to
	PTHREAD_MUTEX_NORMAL - ie. mutexes should no longer
	be recursive by default, and a thread will deadlock if it
	tries to relock a mutex it already owns. This is inline with
	other pthreads implementations.
	* (pthread_mutex_lock): Process the lock request
	according to the mutex type.
	* (pthread_mutex_init): Eliminate use of Win32 mutexes as the
	basis of POSIX mutexes - instead, a combination of one critical section
	and one semaphore are used in conjunction with Win32 Interlocked* routines.
	* (pthread_mutex_destroy): Likewise.
	* (pthread_mutex_lock): Likewise.
	* (pthread_mutex_trylock): Likewise.
	* (pthread_mutex_unlock): Likewise.
	* Use longjmp/setjmp to implement cancellation when building the library
	using a C compiler which doesn't support exceptions, e.g. gcc -x c (note
	that gcc -x c++ uses exceptions).
	* Also fixed some of the same typos and eliminated PT_STDCALL as
	Milan Gardian's patches above.

2001-02-07  Alexander Terekhov <TEREKHOV at de.ibm.com>

	* rwlock.c: Revamped.
	* implement.h (pthread_rwlock_t_): Redefined.
	This implementation does not have reader/writer starvation problem.
	Rwlock attempts to behave more like a normal mutex with
	races and scheduling policy determining who is more important;
	It also supports recursive locking,
	has less synchronization overhead (no broadcasts at all,
	readers are not blocked on any condition variable) and seem to
	be faster than the current implementation [W98 appears to be
	approximately 15 percent faster at least - on top of speed increase
	from Thomas Pfaff's changes to mutex.c - rpj].

2000-12-29  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* Makefile: Back-out "for" loops which don't work.

	* GNUmakefile: Remove the fake.a target; add the "realclean"
	target; don't remove built libs under the "clean" target.

	* config.h: Add a guard against multiple inclusion.

	* semaphore.h: Add some defines from config.h to make
	semaphore.h independent of config.h when building apps.

	* pthread.h (_errno): Back-out previous fix until we know how to
	fix it properly.

	* implement.h (lockCount): Add missing element to pthread_mutex_t_.

	* sync.c (pthread_join): Spelling fix in comment.

	* private.c (ptw32_threadStart): Reset original termination
	function (C++).
	(ptw32_threadStart): Cleanup detached threads early in case
	the library is statically linked.
	(ptw32_callUserDestroyRoutines): Remove [SEH] __try block from
	destructor call so that unhandled exceptions will be passed through
	to the 	system; call terminate() from [C++] try block for the same
	reason.

	* tsd.c (pthread_getspecific): Add comment.

	* mutex.c (pthread_mutex_init): Initialise new elements in
	pthread_mutex_t.
	(pthread_mutex_unlock): Invert "pthread_equal()" test.

2000-12-28  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* semaphore.c (mode_t): Use ifndef HAVE_MODE_T to include definition.

	* config.h.in (HAVE_MODE_T): Added.
	(_UWIN): Start adding defines for the UWIN package.

	* private.c (ptw32_threadStart): Unhandled exceptions are
	now passed through to the system to deal with. This is consistent
	with normal Windows behaviour. C++ applications may use
	set_terminate() to override the default behaviour which is
	to call ptw32_terminate(). Ptw32_terminate() cleans up some
	POSIX thread stuff before calling the system default function
	which calls abort(). The users termination function should conform
	to standard C++ semantics which is to not return. It should
	exit the thread (call pthread_exit()) or exit the application.
	* private.c (ptw32_terminate): Added as the default set_terminate()
	function. It calls the system default function after cleaning up
	some POSIX thread stuff.

	* implement.h (ptw32_try_enter_critical_section): Move
	declaration.
	* global.c (ptw32_try_enter_critical_section): Moved
	from dll.c.
	* dll.c: Move process and thread attach/detach code into
	functions in nonportable.c.
	* nonportable.c (pthread_win32_process_attach_np): Process
	attach code from dll.c is now available to static linked
	applications.
	* nonportable.c (pthread_win32_process_detach_np): Likewise.
	* nonportable.c (pthread_win32_thread_attach_np): Likewise.
	* nonportable.c (pthread_win32_thread_detach_np): Likewise.

	* pthread.h: Add new non-portable prototypes for static
	linked applications.

	* GNUmakefile (OPT): Increase optimisation flag and remove
	debug info flag.

	* pthread.def: Add new non-portable exports for static
	linked applications.

2000-12-11  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* FAQ: Update Answer 6 re getting a fully working
	Mingw32 built library.

2000-10-10  Steven Reddie <smr at essemer.com.au>
 
        * misc.c (pthread_self): Restore Win32 "last error"
        cleared by TlsGetValue() call in
        pthread_getspecific()
 
2000-09-20  Arthur Kantor <akantor at bexusa.com>
 
        * mutex.c (pthread_mutex_lock): Record the owner
        of the mutex. This requires also keeping count of
        recursive locks ourselves rather than leaving it
        to Win32 since we need to know when to NULL the
        thread owner when the mutex is unlocked.
        (pthread_mutex_trylock): Likewise.
        (pthread_mutex_unlock): Check that the calling
        thread owns the mutex, decrement the recursive
        lock count, and NULL the owner if zero. Return
        EPERM if the mutex is owned by another thread.
        * implement.h (pthread_mutex_t_): Add ownerThread
        and lockCount members.

2000-09-13  Jef Gearhart <jgearhart at tpssys.com>

	* mutex.c (pthread_mutex_init): Call
	TryEnterCriticalSection through the pointer
	rather than directly so that the dll can load
	on Windows versions that can't resolve the
	function, eg. Windows 95

2000-09-09  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* pthread.h (ctime_r): Fix arg.

2000-09-08  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* GNUmakefile(_WIN32_WINNT=0x400): Define in CFLAGS;
	doesn't seem to be needed though.

	* cancel.c (pthread_cancel): Must get "self" through
	calling pthread_self() which will ensure a POSIX thread
	struct is built for non-POSIX threads; return an error
	if this fails
	- Ollie Leahy <ollie at mpt.ie>
	(pthread_setcancelstate): Likewise.
	(pthread_setcanceltype): Likewise.
	* misc.c (ptw32_cancelable_wait): Likewise.

	* private.c (ptw32_tkAssocCreate): Remove unused #if 0
	wrapped code.

	* pthread.h (ptw32_get_exception_services_code):
	Needed to be forward declared unconditionally.

2000-09-06  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* cancel.c (pthread_cancel): If called from the main
	thread "self" would be NULL; get "self" via pthread_self()
	instead of directly from TLS so that an implicit
	pthread object is created.

	* misc.c (pthread_equal): Strengthen test for NULLs.

2000-09-02  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* condvar.c (ptw32_cond_wait_cleanup): Ensure that all
	waking threads check if they are the last, and notify
	the broadcaster if so - even if an error occurs in the
	waiter.

	* semaphore.c (_decrease_semaphore): Should be
	a call to ptw32_decrease_semaphore.
	(_increase_semaphore): Should be a call to
	ptw32_increase_semaphore.

	* misc.c (ptw32_cancelable_wait): Renamed from
	CancelableWait.
	* rwlock.c (_rwlock_check*): Renamed to
	ptw32_rwlock_check*.
	* mutex.c (_mutex_check*): Renamed to ptw32_mutex_check*.
	* condvar.c (cond_timed*): Renamed to ptw32_cond_timed*.
	(_cond_check*): Renamed to ptw32_cond_check*.
	(cond_wait_cleanup*): Rename to ptw32_cond_wait_cleanup*.
	(ptw32_cond_timedwait): Add comments.

2000-08-22  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* private.c (ptw32_throw): Fix exception test;
	move exceptionInformation declaration.

	* tsd.c (pthread_key_create): newkey wrongly declared.

	* pthread.h: Fix comment block.

2000-08-18  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* mutex.c (pthread_mutex_destroy): Check that the mutex isn't
	held; invalidate the mutex as early as possible to avoid
	contention; not perfect - FIXME!

	* rwlock.c (pthread_rwlock_init): Remove redundant assignment
	to "rw".
	(pthread_rwlock_destroy): Invalidate the rwlock before
	freeing up any of it's resources - to avoid contention.

	* private.c (ptw32_tkAssocCreate): Change assoc->lock
	to use a dynamically initialised mutex - only consumes
	a W32 mutex or critical section when first used,
	not before.

	* mutex.c (pthread_mutex_init): Remove redundant assignment
	to "mx".
	(pthread_mutexattr_destroy): Set attribute to NULL
	before freeing it's memory - to avoid contention.

	* implement.h  (PTW32_EPS_CANCEL/PTW32_EPS_EXIT):
	Must be defined for all compilers - used as generic
	exception selectors by ptw32_throw().

	* Several: Fix typos from scripted edit session
	yesterday.

	* nonportable.c (pthread_mutexattr_setforcecs_np):
	Moved this function from mutex.c.
	(pthread_getw32threadhandle_np): New function to
	return the win32 thread handle that the POSIX
	thread is using.
	* mutex.c (pthread_mutexattr_setforcecs_np):
	Moved to new file "nonportable.c".

	* pthread.h  (PTW32_BUILD): Only	redefine __except
	and catch compiler keywords if we aren't building
	the library (ie.  PTW32_BUILD is not defined) - 
	this is safer than defining and then undefining
	if not building the library.
	* implement.h: Remove __except and catch undefines.
	* Makefile (CFLAGS): Define  PTW32_BUILD.
	* GNUmakefile (CFLAGS): Define  PTW32_BUILD.

	* All appropriate: Change Pthread_exception* to
	ptw32_exception* to be consistent with internal
	identifier naming.

	* private.c (ptw32_throw): New function to provide
	a generic exception throw for all internal
	exceptions and EH schemes.
	(ptw32_threadStart): pthread_exit() value is now
	returned via the thread structure exitStatus
	element.
	* exit.c (pthread_exit): pthread_exit() value is now
	returned via the thread structure exitStatus
	element.
	* cancel.c (ptw32_cancel_self): Now uses ptw32_throw.
	(pthread_setcancelstate): Ditto.
	(pthread_setcanceltype): Ditto.
	(pthread_testcancel): Ditto.
	(pthread_cancel): Ditto.
	* misc.c (CancelableWait): Ditto.
	* exit.c (pthread_exit): Ditto.
	* All applicable: Change  PTW32_ prefix to
	PTW32_ prefix to remove leading underscores
	from private library identifiers.

2000-08-17  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* All applicable: Change _pthread_ prefix to
	ptw32_ prefix to remove leading underscores
	from private library identifiers (single
	and double leading underscores are reserved in the
	ANSI C standard for compiler implementations).

	* tsd.c (pthread_create_key): Initialise temporary
	key before returning it's address to avoid race
	conditions.

2000-08-13  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* errno.c: Add _MD precompile condition; thus far
	had no effect when using /MD compile option but I
	thnk it should be there.

	* exit.c: Add __cplusplus to various #if lines;
	was compiling SEH code even when VC++ had
	C++ compile options.

	* private.c: ditto.

	* create.c (pthread_create): Add PT_STDCALL macro to
	function pointer arg in _beginthread().

	* pthread.h: PT_STDCALL really does need to be defined
	in both this and impliment.h; don't set it to __cdecl
	- this macro is only used to extend function pointer
	casting for functions that will be passed as parameters.
	(~PThreadCleanup): add cast and group expression.
	(_errno): Add _MD compile conditional.
	(__PtW32NoCatchWarn): Change pragma message.

	* implement.h: Move and change PT_STDCALL define.

	* need_errno.h: Add _MD to compilation conditional.

	* GNUmakefile: Substantial rewrite for new naming
	convention; set for nil optimisation (turn it up
	when we have a working library build; add target
	"fake.a" to build a libpthreadw32.a from the VC++
	built DLL pthreadVCE.dll.

	* pthread.def (LIBRARY): Don't specify in the .def
	file - it is specified on the linker command line
	since we now use the same .def file for variously
	named .dlls.

	* Makefile: Substantial rewrite for new naming
	convention; default nmake target only issues a
	help message; run nmake with specific target
	corresponding to the EH scheme being used.

	* README: Update information; add naming convention
	explanation.

	* ANNOUNCE: Update information.

2000-08-12  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* pthread.h: Add compile-time message when using
	MSC_VER compiler and C++ EH to warn application
	programmers to use __PtW32Catch instead of catch(...)
	if they want cancellation and pthread_exit to work.

	* implement.h: Remove #include <semaphore.h>; we
	use our own local semaphore.h.

2000-08-10  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* cleanup.c (pthread_pop_cleanup): Remove _pthread
	prefix from __except and catch keywords; implement.h
	now simply undefines ptw32__except and
	ptw32_catch if defined; VC++ was not textually
	substituting ptw32_catch etc back to catch as
	it was redefined; the reason for using the prefixed
	version was to make it clear that it was not using
	the pthread.h redefined catch keyword.

	* private.c (ptw32_threadStart): Ditto.
	(ptw32_callUserDestroyRoutines): Ditto.

	* implement.h (ptw32__except): Remove #define.
	(ptw32_catch): Remove #define.

	* GNUmakefile (pthread.a): New target to build
	libpthread32.a from pthread.dll using dlltool.

	* buildlib.bat: Duplicate cl commands with args to
	build C++ EH version of pthread.dll; use of .bat
	files is redundant now that nmake compatible
	Makefile is included; used as a kludge only now.

	* Makefile: Localise some macros and fix up the clean:
	target to extend it and work properly.

	* CONTRIBUTORS: Add contributors.

	* ANNOUNCE: Updated.

	* README: Updated.

2000-08-06  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* pthread.h: Remove #warning - VC++ doesn't accept it.

2000-08-05  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* pthread.h (__PtW32CatchAll): Add macro. When compiling
	applications using VC++ with C++ EH rather than SEH
	'__PtW32CatchAll' must be used in place of any 'catch( ... )'
	if the application wants pthread cancellation or
	pthread_exit() to work.

2000-08-03  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* pthread.h: Add a base class ptw32_exception for
	library internal exceptions and change the "catch"
	re-define macro to use it.

2000-08-02  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* GNUmakefile (CFLAGS): Add -mthreads.
	Add new targets to generate cpp and asm output.

	* sync.c (pthread_join): Remove dead code.

2000-07-25  Tristan Savatier <tristan at mpegtv.com>

	* sched.c (sched_get_priority_max): Handle different WinCE and
	Win32 priority values together.
	(sched_get_priority_min): Ditto.

2000-07-25  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* create.c (pthread_create): Force new threads to wait until
	pthread_create has the new thread's handle; we also retain
	a local copy of the handle for internal use until
	pthread_create returns.

	* private.c (ptw32_threadStart): Initialise ei[].
	(ptw32_threadStart): When beginthread is used to start the
	thread, force waiting until the creator thread had the 
	thread handle.

	* cancel.c (ptw32_cancel_thread): Include context switch
	code for defined(_X86_) environments in addition to _M_IX86.

	* rwlock.c (pthread_rwlock_destroy): Assignment changed
	to avoid compiler warning.

	* private.c (ptw32_get_exception_services_code): Cast
	NULL return value to avoid compiler warning.

	* cleanup.c (pthread_pop_cleanup): Initialise "cleanup" variable
	to avoid compiler warnings.

	* misc.c (ptw32_new): Change "new" variable to "t" to avoid
	confusion with the C++ keyword of the same name.

	* condvar.c (cond_wait_cleanup): Initialise lastWaiter variable.
	(cond_timedwait): Remove unused local variables. to avoid
	compiler warnings.

	* dll.c (dllMain): Remove 2000-07-21 change - problem
	appears to be in pthread_create().

2000-07-22  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* tsd.c (pthread_key_create): If a destructor was given
	and the pthread_mutex_init failed, then would try to
	reference a NULL pointer (*key); eliminate this section of
	code by using a dynamically initialised mutex
	(PTHREAD_MUTEX_INITIALIZER).

	* tsd.c (pthread_setspecific): Return an error if
	unable to set the value; simplify cryptic conditional.

	* tsd.c (pthread_key_delete): Locking threadsLock relied
	on mutex_lock returning an error if the key has no destructor.
	ThreadsLock is only initialised if the key has a destructor.
	Making this mutex a static could reduce the number of mutexes
	used by an application since it is actually created only at
	first use and it's often destroyed soon after.
	
2000-07-22  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* FAQ: Added Q5 and Q6.

2000-07-21  David Baggett <dmb at itasoftware.com>

	* dll.c: Include resource leakage work-around. This is a
	partial FIXME which doesn't stop all leakage. The real
	problem needs to be found and fixed.

2000-07-21  Ross Johnson  <rpj at setup1.ise.canberra.edu.au>

	* create.c (pthread_create): Set threadH to 0 (zero)
	everywhere. Some assignments were using NULL. Maybe
	it should be NULL everywhere - need to check. (I know
	they are nearly always the same thing - but not by
	definition.)

	* misc.c (pthread_self): Try to catch NULL thread handles
	at the point where they might be generated, even though
	they should always be valid at this point.

	* tsd.c (pthread_setspecific): return an error value if
	pthread_self() returns NULL.

	* sync.c (pthread_join): return an error value if
	pthread_self() returns NULL.

	* signal.c (pthread_sigmask): return an error value if
	pthread_self() returns NULL.

2000-03-02  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* attr.c (pthread_attr_init): Set default stacksize to zero (0)
	rather than PTHREAD_STACK_MIN even though these are now the same.

	* pthread.h (PTHREAD_STACK_MIN): Lowered to 0.

2000-01-28  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* mutex.c (pthread_mutex_init): Free mutex if it has been alloced;
	if critical sections can be used instead of Win32 mutexes, test
	that the critical section works and return an error if not.

2000-01-07  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* cleanup.c (pthread_pop_cleanup): Include SEH code only if MSC is not
	compiling as C++.
	(pthread_push_cleanup): Include SEH code only if MSC is not
	compiling as C++.

	* pthread.h: Include SEH code only if MSC is not
	compiling as C++.

	* implement.h: Include SEH code only if MSC is not
	compiling as C++.

	* cancel.c (ptw32_cancel_thread): Add _M_IX86 check.
	(pthread_testcancel): Include SEH code only if MSC is not
	compiling as C++.
	(ptw32_cancel_self): Include SEH code only if MSC is not
	compiling as C++.

2000-01-06  Erik Hensema <erik.hensema at group2000.nl>

	* Makefile: Remove inconsistencies in 'cl' args

2000-01-04  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* private.c (ptw32_get_exception_services_code): New; returns
	value of EXCEPTION_PTW32_SERVICES.
	(ptw32_processInitialize): Remove initialisation of
	ptw32_exception_services which is no longer needed.

	* pthread.h (ptw32_exception_services): Remove extern.
	(ptw32_get_exception_services_code): Add function prototype;
	use this to return EXCEPTION_PTW32_SERVICES value instead of
	using the ptw32_exception_services variable which I had
	trouble exporting through pthread.def.

	* global.c (ptw32_exception_services): Remove declaration.

1999-11-22  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* implement.h: Forward declare ptw32_new();

	* misc.c (ptw32_new): New; alloc and initialise a new pthread_t.
	(pthread_self): New thread struct is generated 	by new routine
	ptw32_new().

	* create.c (pthread_create): New thread struct is generated
	by new routine ptw32_new().

1999-11-21  Ross Johnson  <rpj at special.ise.canberra.edu.au>

	* global.c (ptw32_exception_services): Declare new variable. 

	* private.c (ptw32_threadStart): Destroy thread's
	cancelLock mutex; make 'catch' and '__except' usageimmune to
	redfinitions in pthread.h.
	(ptw32_processInitialize): Init new constant ptw32_exception_services.

	* create.c (pthread_create): Initialise thread's cancelLock
	mutex.

	* cleanup.c (pthread_pop_cleanup): Make 'catch' and '__except'
	usage immune to redfinition s in pthread.h.

	* private.c: Ditto.

	* pthread.h (catch): Redefine 'catch' so that C++ applications
	won't catch our internal exceptions.
	(__except): ditto for __except.

	* implement.h (ptw32_catch): Define internal version
	of 'catch' because 'catch' is redefined by pthread.h.
	(__except): ditto for __except.
	(struct pthread_t_): Add cancelLock mutex for async cancel
	safety.

1999-11-21  Jason Nye <jnye at nbnet.nb.ca>, Erik Hensema <erik.hensema at group2000.nl>

	* cancel.c (ptw32_cancel_self): New; part of the async
	cancellation implementation.
	(ptw32_cancel_thread): Ditto; this function is X86
	processor specific.
	(pthread_setcancelstate): Add check for pending async
	cancel request and cancel the calling thread if
	required; add async-cancel safety lock.
	(pthread_setcanceltype): Ditto.

1999-11-13  Erik Hensema <erik.hensema at group2000.nl>

	* configure.in (AC_OUTPUT): Put generated output into GNUmakefile
	rather than Makefile. Makefile will become the MSC nmake compatible
	version

1999-11-13  John Bossom (John.Bossom@gmail.com>

	* misc.c (pthread_self): Add a note about GetCurrentThread
	returning a pseudo-handle

1999-11-10  Todd Owen <towen at lucidcalm.dropbear.id.au>

	* dll.c (dllMain): Free kernel32 ASAP.
	If TryEnterCriticalSection is not being used, then free
	the kernel32.dll handle now, rather than leaving it until
	DLL_PROCESS_DETACH.

	Note: this is not a pedantic exercise in freeing unused
	resources!  It is a work-around for a bug in Windows 95
	(see microsoft knowledge base article, Q187684) which
	does Bad Things when FreeLibrary is called within
	the DLL_PROCESS_DETACH code, in certain situations.
	Since w95 just happens to be a platform which does not
	provide TryEnterCriticalSection, the bug will be
	effortlessly avoided.

1999-11-10  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* sync.c (pthread_join): Make it a deferred cancellation point.

	* misc.c (pthread_self): Explicitly initialise implicitly
	created thread state to default values.

1999-11-05  Tristan Savatier <tristan at mpegtv.com>

	* pthread.h (winsock.h): Include unconditionally.
	(ETIMEDOUT): Change fallback value to that defined by winsock.h.
	
	* general: Patched for portability to WinCE. The details are
	described in the file WinCE-PORT. Follow the instructions
	in README.WinCE to make the appropriate changes in config.h.

1999-10-30  Erik Hensema <erik.hensema at group2000.nl>

	* create.c (pthread_create): Explicitly initialise thread state to
	default values.

	* cancel.c (pthread_setcancelstate): Check for NULL 'oldstate'
	for compatibility with Solaris pthreads;
	(pthread_setcanceltype): ditto:

1999-10-23  Erik Hensema <erik.hensema at group2000.nl>

	* pthread.h (ctime_r): Fix incorrect argument "_tm"

1999-10-21  Aurelio Medina <aureliom at crt.com>

	* pthread.h (_POSIX_THREADS): Only define it if it isn't
	already defined. Projects may need to define this on
	the CC command line under Win32 as it doesn't have unistd.h

1999-10-17  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* rwlock.c (pthread_rwlock_destroy): Add cast to remove compile
	warning.

	* condvar.c (pthread_cond_broadcast): Only release semaphores
	if there are waiting threads.

1999-10-15  Lorin Hochstein <lmh at xiphos.ca>, Peter Slacik <Peter.Slacik at tatramed.sk>

	* condvar.c (cond_wait_cleanup): New static cleanup handler for
	cond_timedwait;
	(cond_timedwait): pthread_cleanup_push args changed;
	canceling a thread while it's in pthread_cond_wait
	will now decrement the waiters count and cleanup if it's the
	last waiter.

1999-10-15  Graham Dumpleton <Graham.Dumpleton at ra.pad.otc.telstra.com.au>

	* condvar.c (cond_wait_cleanup): the last waiter will now reset the CV's
	wasBroadcast flag

Thu Sep 16 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* rwlock.c (pthread_rwlock_destroy): Add serialisation.
	(_rwlock_check_need_init): Check for detroyed rwlock.
	* rwlock.c: Check return codes from _rwlock_check_need_init();
	modify comments; serialise access to rwlock objects during
	operations; rename rw_mutex to rw_lock.
	* implement.h: Rename rw_mutex to rw_lock.
	* mutex.c (pthread_mutex_destroy): Add serialisation.
	(_mutex_check_need_init): Check for detroyed mutex.
	* condvar.c (pthread_cond_destroy): Add serialisation.
	(_cond_check_need_init): Check for detroyed condvar.
	* mutex.c: Modify comments.
	* condvar.c: Modify comments.

1999-08-10  Aurelio Medina  <aureliom at crt.com>

	* implement.h (pthread_rwlock_t_): Add.
	* pthread.h (pthread_rwlock_t): Add.
	(PTHREAD_RWLOCK_INITIALIZER): Add.
	Add rwlock function prototypes.
	* rwlock.c: New module.
	* pthread.def: Add new rwlock functions.
	* private.c (ptw32_processInitialize): initialise
	ptw32_rwlock_test_init_lock critical section.
	* global.c (ptw32_rwlock_test_init_lock): Add.

	* mutex.c (pthread_mutex_destroy): Don't free mutex memory
	if mutex is PTHREAD_MUTEX_INITIALIZER and has not been
	initialised yet.

1999-08-08 Milan Gardian <mg at tatramed.sk>

	* mutex.c (pthread_mutex_destroy): Free mutex memory.

1999-08-22  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* exit.c (pthread_exit): Fix reference to potentially
	uninitialised pointer.

1999-08-21  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c (ptw32_threadStart): Apply fix of 1999-08-19
	this time to C++ and non-trapped C versions. Ommitted to
	do this the first time through.

1999-08-19  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c (ptw32_threadStart): Return exit status from
	the application thread startup routine.
	- Milan Gardian <mg at tatramed.sk>

1999-08-18  John Bossom <john.Bossom at gmail.com>

	* exit.c (pthread_exit): Put status into pthread_t->exitStatus
	* private.c (ptw32_threadStart): Set pthread->exitStatus
	on exit of try{} block.
	* sync.c (pthread_join): use pthread_exitStatus value if the
	thread exit doesn't return a value (for Mingw32 CRTDLL
	which uses endthread instead of _endthreadex).

Tue Aug 17 20:17:58 CDT 1999  Mumit Khan  <khan at xraylith.wisc.edu>

        * create.c (pthread_create): Add CRTDLL suppport.
        * exit.c (pthread_exit): Likewise.
        * private.c (ptw32_threadStart): Likewise.
        (ptw32_threadDestroy): Likewise.
        * sync.c (pthread_join): Likewise.
        * tests/join1.c (main): Warn about partial support for CRTDLL.

Tue Aug 17 20:00:08 1999  Mumit Khan  <khan at xraylith.wisc.edu>

        * Makefile.in (LD): Delete entry point.
        * acconfig.h (STDCALL): Delete unused macro.
        * configure.in: Remove test for STDCALL.
        * config.h.in: Regenerate.
        * errno.c (_errno): Fix self type.
        * pthread.h (PT_STDCALL): Move from here to
        * implement.h (PT_STDCALL): here.
        (ptw32_threadStart): Fix prototype.
        * private.c (ptw32_threadStart): Likewise.

1999-08-14  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* exit.c (pthread_exit): Don't call pthread_self() but
	get thread handle directly from TSD for efficiency.
	
1999-08-12  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c (ptw32_threadStart): ei[] only declared if _MSC_VER.

	* exit.c (pthread_exit): Check for implicitly created threads
	to avoid raising an unhandled exception.
	
1999-07-12  Peter Slacik <Peter.Slacik at tatramed.sk>

	* condvar.c (pthread_cond_destroy): Add critical section.
	(cond_timedwait): Add critical section; check for timeout
	waiting on semaphore.
	(pthread_cond_broadcast): Add critical section.

1999-07-09  Lorin Hochstein <lmh at xiphos.ca>, John Bossom <John.Bossom at Cognos.COM>

	The problem was that cleanup handlers were not executed when
	pthread_exit() was called.

	* implement.h (pthread_t_): Add exceptionInformation element for
	C++ per-thread exception information.
	(general): Define and rename exceptions.

1999-07-09  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* misc.c (CancelableWait):   PTW32_EPS_CANCEL (SEH) and
	ptw32_exception_cancel (C++) used to identify the exception.

	* cancel.c (pthread_testcancel):  PTW32_EPS_CANCEL (SEH) and
	ptw32_exception_cancel (C++) used to identify the exception.

	* exit.c (pthread_exit): throw/raise an exception to return to
	ptw32_threadStart() to exit the thread.  PTW32_EPS_EXIT (SEH)
	and ptw32_exception_exit (C++) used to identify the exception.

	* private.c (ptw32_threadStart): Add pthread_exit exception trap;
	clean up and exit the thread directly rather than via pthread_exit().

Sun May 30 00:25:02 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* semaphore.h (mode_t): Conditionally typedef it.

Fri May 28 13:33:05 1999  Mark E. Armstrong <avail at pacbell.net>

	* condvar.c (pthread_cond_broadcast): Fix possible memory fault
	
Thu May 27 13:08:46 1999  Peter Slacik <Peter.Slacik at tatramed.sk>

	* condvar.c (pthread_cond_broadcast): Fix logic bug

Thu May 27 13:08:46 1999  Bossom, John <John.Bossom at Cognos.COM>

	* condvar.c (pthread_cond_broadcast): optimise sem_post loop

Fri May 14 12:13:18 1999  Mike Russo <miker at eai.com>

	* attr.c (pthread_attr_setdetachstate): Fix logic bug

Sat May  8 09:42:30 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.def (sem_open): Add.
	(sem_close): Add.
	(sem_unlink): Add.
	(sem_getvalue): Add.

	* FAQ (Question 3): Add.

Thu Apr  8 01:16:23 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* semaphore.c (sem_open): New function; returns an error (ENOSYS).
	(sem_close): ditto.
	(sem_unlink): ditto.
	(sem_getvalue): ditto.

	* semaphore.h (_POSIX_SEMAPHORES): define.
	
Wed Apr  7 14:09:52 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* errno.c (_REENTRANT || _MT): Invert condition.

	* pthread.h (_errno): Conditionally include prototype.

Wed Apr  7 09:37:00 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* *.c (comments): Remove individual attributions - these are
	documented sufficiently elsewhere.

	* implement.h (pthread.h): Remove extraneous include.

Sun Apr  4 11:05:57 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* sched.c (sched.h): Include.

	* sched.h: New file for POSIX 1b scheduling.

	* pthread.h: Move opaque structures to implement.h; move sched_*
	prototypes out and into sched.h.

	* implement.h: Add opaque structures from pthread.h.

	* sched.c (sched_yield): New function.

	* condvar.c (ptw32_sem_*): Rename to sem_*; except for
	ptw32_sem_timedwait which is an private function.

Sat Apr  3 23:28:00 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* Makefile.in (OBJS): Add errno.o.

Fri Apr  2 11:08:50 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h (ptw32_sem_*): Remove prototypes now defined in
	semaphore.h.

	* pthread.h (sempahore.h): Include.

	* semaphore.h: New file for POSIX 1b semaphores.

	* semaphore.c (ptw32_sem_timedwait): Moved to private.c.

	* pthread.h (ptw32_sem_t): Change to sem_t. 

	* private.c (ptw32_sem_timedwait): Moved from semaphore.c;
	set errno on error.

	* pthread.h (pthread_t_): Add per-thread errno element.

Fri Apr  2 11:08:50 1999  John Bossom <john.bossom at gmail.com>

	* semaphore.c (ptw32_sem_*): Change to sem_*; these functions
	will be exported from the library; set errno on error.

	* errno.c (_errno): New file. New function.

Fri Mar 26 14:11:45 1999  Tor Lillqvist <tml at iki.fi>

	* semaphore.c (ptw32_sem_timedwait): Check for negative
	milliseconds.

Wed Mar 24 11:32:07 1999  John Bossom <john.bossom at gmail.com>

	* misc.c (CancelableWait): Initialise exceptionInformation[2].
	(pthread_self): Get a real Win32 thread handle for implicit threads.

	* cancel.c (pthread_testcancel): Initialise exceptionInformation[2].

	* implement.h (SE_INFORMATION): Fix values.

	* private.c (ptw32_threadDestroy): Close the thread handle.

Fri Mar 19 12:57:27 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* cancel.c (comments): Update and cleanup.

Fri Mar 19 09:12:59 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c (ptw32_threadStart): status returns PTHREAD_CANCELED.

	* pthread.h (PTHREAD_CANCELED): defined.

Tue Mar 16  1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* all: Add GNU LGPL and Copyright and Warranty.
	
Mon Mar 15 00:20:13 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* condvar.c (pthread_cond_init): fix possible uninitialised use
	of cv.

Sun Mar 14 21:01:59 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* condvar.c (pthread_cond_destroy): don't do full cleanup if
	static initialised cv has never been used.
	(cond_timedwait): check result of auto-initialisation.

Thu Mar 11 09:01:48 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.h (pthread_mutex_t): revert to (pthread_mutex_t *);
	define a value to serve as PTHREAD_MUTEX_INITIALIZER.
	(pthread_mutex_t_): remove staticinit and valid elements.
	(pthread_cond_t): revert to (pthread_cond_t_ *);
	define a value to serve as PTHREAD_COND_INITIALIZER.
	(pthread_cond_t_): remove staticinit and valid elements.

	* mutex.c (pthread_mutex_t args): adjust indirection of references.
	(all functions): check for PTHREAD_MUTEX_INITIALIZER value;
	check for NULL (invalid).

	* condvar.c (pthread_cond_t args): adjust indirection of references.
	(all functions): check for PTHREAD_COND_INITIALIZER value;
	check for NULL (invalid).

Wed Mar 10 17:18:12 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* misc.c (CancelableWait): Undo changes from Mar 8 and 7.

Mon Mar  8 11:18:59 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* misc.c (CancelableWait): Ensure cancelEvent handle is the lowest
	indexed element in the handles array. Enhance test for abandoned
	objects.

	* pthread.h (PTHREAD_MUTEX_INITIALIZER): Trailing elements not
	initialised are set to zero by the compiler. This avoids the
	problem of initialising the opaque critical section element in it.
	(PTHREAD_COND_INITIALIZER): Ditto.

	* semaphore.c (ptw32_sem_timedwait): Check sem == NULL earlier.

Sun Mar  7 12:31:14 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* condvar.c (pthread_cond_init): set semaphore initial value
	to 0, not 1. cond_timedwait was returning signaled immediately.

	* misc.c (CancelableWait): Place the cancel event handle first
	in the handle table for WaitForMultipleObjects. This ensures that
	the cancel event is recognised and acted apon if both objects
	happen to be signaled together.

	* private.c (ptw32_cond_test_init_lock): Initialise and destroy.

	* implement.h (ptw32_cond_test_init_lock): Add extern.

	* global.c (ptw32_cond_test_init_lock): Add declaration. 

	* condvar.c (pthread_cond_destroy): check for valid initialised CV;
	flag destroyed CVs as invalid.
	(pthread_cond_init): pthread_cond_t is no longer just a pointer.
	This is because PTHREAD_COND_INITIALIZER needs state info to reside
	in pthread_cond_t so that it can initialise on first use. Will work on
	making pthread_cond_t (and other objects like it) opaque again, if
	possible, later.
	(cond_timedwait): add check for statically initialisation of
	CV; initialise on first use.
	(pthread_cond_signal): check for valid CV.
	(pthread_cond_broadcast): check for valid CV.
	(_cond_check_need_init): Add.

	* pthread.h (PTHREAD_COND_INITIALIZER): Fix.
	(pthread_cond_t): no longer a pointer to pthread_cond_t_.
	(pthread_cond_t_): add 'staticinit' and 'valid' elements.

Sat Mar 6 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h: Undate comments.

Sun Feb 21 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.h (PTHREAD_MUTEX_INITIALIZER): missing braces around
	cs element initialiser.

1999-02-21  Ben Elliston  <bje at cygnus.com>

	* pthread.h (pthread_exit): The return type of this function is
	void, not int.

	* exit.c (pthread_exit): Do not return 0.

Sat Feb 20 16:03:30 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* dll.c (DLLMain): Expand TryEnterCriticalSection support test.

	* mutex.c (pthread_mutex_trylock): The check for
	ptw32_try_enter_critical_section == NULL should have been
	removed long ago.

Fri Feb 19 16:03:30 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* sync.c (pthread_join): Fix pthread_equal() test.

	* mutex.c (pthread_mutex_trylock): Check mutex != NULL before
	using it.

Thu Feb 18 16:17:30 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* misc.c (pthread_equal): Fix inverted result.

	* Makefile.in: Use libpthread32.a as the name of the DLL export
	library instead of pthread.lib.

	* condvar.c (pthread_cond_init): cv could have been used unitialised;
	initialise.

	* create.c (pthread_create): parms could have been used unitialised;
	initialise.

	* pthread.h (struct pthread_once_t_): Remove redefinition.

Sat Feb 13 03:03:30 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.h (struct pthread_once_t_): Replaced.

	* misc.c (pthread_once): Replace with John Bossom's version;
	has lighter weight serialisation; fixes problem of not holding
	competing threads until after the init_routine completes.

Thu Feb 11 13:34:14 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* misc.c (CancelableWait): Change C++ exception throw.

	* sync.c (pthread_join): Change FIXME comment - issue resolved.

Wed Feb 10 12:49:11 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* configure: Various temporary changes.
	- Kevin Ruland <Kevin.Ruland at anheuser-busch.com>

	* README: Update.

	* pthread.def (pthread_attr_getstackaddr): uncomment
	(pthread_attr_setstackaddr): uncomment

Fri Feb  5 13:42:30 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* semaphore.c: Comment format changes.

Thu Feb  4 10:07:28 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* global.c: Remove ptw32_exception instantiation.

	* cancel.c (pthread_testcancel): Change C++ exception throw.

	* implement.h: Remove extern declaration.

Wed Feb  3 13:04:44 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* cleanup.c: Rename ptw32_*_cleanup() to pthread_*_cleanup().

	* pthread.def: Ditto.
	
	* pthread.h: Ditto.

	* pthread.def (pthread_cleanup_push): Remove from export list;
	the function is defined as a macro under all compilers.
	(pthread_cleanup_pop): Ditto.

	* pthread.h: Remove #if defined().

Wed Feb  3 10:13:48 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* sync.c (pthread_join): Check for NULL value_ptr arg;
	check for detached threads.

Tue Feb  2 18:07:43 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* implement.h: Add #include <pthread.h>.
	Change sem_t to ptw32_sem_t.

Tue Feb  2 18:07:43 1999  Kevin Ruland <Kevin.Ruland at anheuser-busch.com>

	* signal.c (pthread_sigmask): Add and modify casts.
	Reverse LHS/RHS bitwise assignments.

	* pthread.h: Remove #include <semaphore.h>.
	 (PTW32_ATTR_VALID): Add cast.
	(struct pthread_t_): Add sigmask element.

	* dll.c: Add "extern C" for DLLMain.
	(DllMain): Add cast.

	* create.c (pthread_create): Set sigmask in thread.

	* condvar.c: Remove #include. Change sem_* to ptw32_sem_*.

	* attr.c: Changed #include.

	* Makefile.in: Additional targets and changes to build the library
	as a DLL.

Fri Jan 29 11:56:28 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* Makefile.in (OBJS): Add semaphore.o to list.

	* semaphore.c (ptw32_sem_timedwait): Move from private.c.
	Rename sem_* to ptw32_sem_*.

	* pthread.h (pthread_cond_t): Change type of sem_t.
	_POSIX_SEMAPHORES no longer defined.

	* semaphore.h: Contents moved to implement.h.
	Removed from source tree.

	* implement.h: Add semaphore function prototypes and rename all
	functions to prepend 'ptw32_'. They are
	now private to the pthreads-win32 implementation.

	* private.c: Change #warning.
	Move ptw32_sem_timedwait() to semaphore.c.

	* cleanup.c: Change #warning.

	* misc.c: Remove #include <errno.h>

	* pthread.def: Cleanup CVS merge conflicts.

	* global.c: Ditto.

	* ChangeLog: Ditto.

	* cleanup.c: Ditto.

Sun Jan 24 01:34:52 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* semaphore.c (sem_wait): Remove second arg to 
	pthreadCancelableWait() call.

Sat Jan 23 17:36:40 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.def: Add new functions to export list.

	* pthread.h (PTHREAD_MUTEX_AUTO_CS_NP): New.
	(PTHREAD_MUTEX_FORCE_CS_NP): New.

	* README: Updated.

Fri Jan 22 14:31:59 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* Makefile.in (CFLAGS): Remove -fhandle-exceptions. Not needed
	with egcs. Add -g for debugging.

	* create.c (pthread_create): Replace __stdcall with PT_STDCALL
	macro. This is a hack and must be fixed.

	* misc.c (CancelableWait): Remove redundant statement.

	* mutex.c (pthread_mutexattr_init): Cast calloc return value.

	* misc.c (CancelableWait): Add cast.
	(pthread_self): Add cast.

	* exit.c (pthread_exit): Add cast.

	* condvar.c (pthread_condattr_init): Cast calloc return value.

	* cleanup.c: Reorganise conditional compilation.

	* attr.c (pthread_attr_init): Remove unused 'result'.
	Cast malloc return value.

	* private.c (ptw32_callUserDestroyRoutines): Redo conditional
	compilation.

	* misc.c (CancelableWait): C++ version uses 'throw'.

	* cancel.c (pthread_testcancel): Ditto.

	* implement.h (class ptw32_exception): Define for C++.

	* pthread.h: Fix C, C++, and Win32 SEH condition compilation
	mayhem around pthread_cleanup_* defines. C++ version now uses John
	Bossom's cleanup handlers.
	(pthread_attr_t): Make 'valid' unsigned.
	Define '_timeb' as 'timeb' for Ming32.
	Define PT_STDCALL as nothing for Mingw32. May be temporary.

	* cancel.c (pthread_testcancel): Cast return value.

Wed Jan 20 09:31:28 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.h (pthread_mutexattr_t): Changed to a pointer.

	* mutex.c (pthread_mutex_init): Conditionally create Win32 mutex
	- from John Bossom's implementation.
	(pthread_mutex_destroy): Conditionally close Win32 mutex
	- from John Bossom's implementation.
	(pthread_mutexattr_init): Replaced by John Bossom's version.
	(pthread_mutexattr_destroy): Ditto.
	(pthread_mutexattr_getpshared): New function from John Bossom's
	implementation.
	(pthread_mutexattr_setpshared): New function from John Bossom's
	implementation.

Tue Jan 19 18:27:42 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* pthread.h (pthreadCancelableTimedWait): New prototype.
	(pthreadCancelableWait): Remove second argument.

	* misc.c (CancelableWait): New static function is 
	pthreadCancelableWait() renamed.
	(pthreadCancelableWait): Now just calls CancelableWait() with
	INFINITE timeout.
	(pthreadCancelableTimedWait): Just calls CancelableWait()
	with passed in timeout.

Tue Jan 19 18:27:42 1999  Scott Lightner <scott at curriculum.com>

	* private.c (ptw32_sem_timedwait): 'abstime' arg really is
	absolute time. Calculate relative time to wait from current
	time before passing timeout to new routine 
	pthreadCancelableTimedWait().

Tue Jan 19 10:27:39 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.h (pthread_mutexattr_setforcecs_np): New prototype.
	
	* mutex.c (pthread_mutexattr_init): Init 'pshared' and 'forcecs'
	attributes to 0.
	(pthread_mutexattr_setforcecs_np): New function (not portable).

	* pthread.h (pthread_mutex_t): 
	Add 'mutex' element. Set to NULL in PTHREAD_MUTEX_INITIALIZER.
	The pthread_mutex_*() routines will try to optimise performance
	by choosing either mutexes or critical sections as the basis
	for pthread mutexes for each indevidual mutex.
	(pthread_mutexattr_t_): Add 'forcecs' element.
	Some applications may choose to force use of critical sections
	if they know that:-
	     the mutex is PROCESS_PRIVATE and, 
	         either the OS supports TryEnterCriticalSection() or
	         pthread_mutex_trylock() will never be called on the mutex.
	This attribute will be setable via a non-portable routine.

	Note: We don't yet support PROCESS_SHARED mutexes, so the
	implementation as it stands will default to Win32 mutexes only if
	the OS doesn't support TryEnterCriticalSection. On Win9x, and early
	versions of NT 'forcecs' will need to be set in order to get
	critical section based mutexes.

Sun Jan 17 12:01:26 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.h (PTHREAD_MUTEX_INITIALIZER): Init new 'staticinit'
	value to '1' and existing 'valid' value to '1'.

	* global.c (ptw32_mutex_test_init_lock): Add.

	* implement.h (ptw32_mutex_test_init_lock.): Add extern.

	* private.c (ptw32_processInitialize): Init critical section for
	global lock used by _mutex_check_need_init().
	(ptw32_processTerminate): Ditto (:s/Init/Destroy/).

	* dll.c (dllMain): Move call to FreeLibrary() so that it is only
	called once when the process detaches.

	* mutex.c (_mutex_check_need_init): New static function to test
	and init PTHREAD_MUTEX_INITIALIZER mutexes. Provides serialised
	access to the internal state of the uninitialised static mutex. 
	Called from pthread_mutex_trylock() and pthread_mutex_lock() which
	do a quick unguarded test to check if _mutex_check_need_init()
	needs to be called. This is safe as the test is conservative
 	and is repeated inside the guarded section of 
	_mutex_check_need_init(). Thus in all calls except the first
	calls to lock static mutexes, the additional overhead to lock any
	mutex is a single memory fetch and test for zero.

	* pthread.h (pthread_mutex_t_): Add 'staticinit' member. Mutexes
	initialised by PTHREAD_MUTEX_INITIALIZER aren't really initialised
	until the first attempt to lock it. Using the 'valid'
	flag (which flags the mutex as destroyed or not) to record this
	information would be messy. It is possible for a statically
	initialised mutex such as this to be destroyed before ever being
	used.

	* mutex.c (pthread_mutex_trylock): Call _mutex_check_need_init()
	to test/init PTHREAD_MUTEX_INITIALIZER mutexes.
	(pthread_mutex_lock): Ditto.
	(pthread_mutex_unlock): Add check to ensure we don't try to unlock
	an unitialised static mutex.
	(pthread_mutex_destroy): Add check to ensure we don't try to delete
	a critical section that we never created. Allows us to destroy
	a static mutex that has never been locked (and hence initialised).
	(pthread_mutex_init): Set 'staticinit' flag to 0 for the new mutex.

Sun Jan 17 12:01:26 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c (ptw32_sem_timedwait): Move from semaphore.c.

	* semaphore.c : Remove redundant #includes.
	(ptw32_sem_timedwait): Move to private.c.
	(sem_wait): Add missing abstime arg to pthreadCancelableWait() call.

Fri Jan 15 23:38:05 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* condvar.c (cond_timedwait): Remove comment.

Fri Jan 15 15:41:28 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* pthread.h: Add new 'abstime' arg to pthreadCancelableWait()
	prototype.

	* condvar.c (cond_timedwait): New generalised function called by
	both pthread_cond_wait() and pthread_cond_timedwait(). This is
	essentially pthread_cond_wait() renamed and modified to add the
	'abstime' arg and call the new ptw32_sem_timedwait() instead of
	sem_wait().
	(pthread_cond_wait): Now just calls the internal static
	function cond_timedwait() with an INFINITE wait.
	(pthread_cond_timedwait): Now implemented. Calls the internal
	static function cond_timedwait().

	* implement.h (ptw32_sem_timedwait): New internal function
	prototype.

	* misc.c (pthreadCancelableWait): Added new 'abstime' argument
	to allow shorter than INFINITE wait.

	* semaphore.c (ptw32_sem_timedwait): New function for internal
	use.  This is essentially sem_wait() modified to add the
        'abstime' arg and call the modified (see above)
        pthreadCancelableWait().

Thu Jan 14 14:27:13 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* cleanup.c: Correct _cplusplus to __cplusplus wherever used.

	* Makefile.in: Add CC=g++ and add -fhandle-exceptions to CFLAGS.
	The derived Makefile will compile all units of the package as C++
	so that those which include try/catch exception handling should work
	properly. The package should compile ok if CC=gcc, however, exception
	handling will not be included and thus thread cancellation, for
 	example, will not work.

	* cleanup.c (ptw32_pop_cleanup): Add #warning to compile this
 	file as C++ if using a cygwin32 environment. Perhaps the whole package
	should be compiled using g++ under cygwin.

	* private.c (ptw32_threadStart): Change #error directive
	into #warning and bracket for __CYGWIN__ and derivative compilers.

Wed Jan 13 09:34:52 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* build.bat: Delete old binaries before compiling/linking.

Tue Jan 12 09:58:38 1999  Tor Lillqvist <tml at iki.fi>

	* dll.c: The Microsoft compiler pragmas probably are more
	appropriately protected by _MSC_VER than by _WIN32.

	* pthread.h: Define ETIMEDOUT. This should be returned by
	pthread_cond_timedwait which is not implemented yet as of
	snapshot-1999-01-04-1305. It was implemented in the older version.
	The Microsoft compiler pragmas probably are more appropriately
	protected by _MSC_VER than by _WIN32.

	* pthread.def: pthread_mutex_destroy was missing from the def file

	* condvar.c (pthread_cond_broadcast): Ensure we only wait on threads
	if there were any waiting on the condition.
	I think pthread_cond_broadcast should do the WaitForSingleObject
	only if cv->waiters > 0? Otherwise it seems to hang, at least in the
	testg thread program from glib.

Tue Jan 12 09:58:38 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* condvar.c (pthread_cond_timedwait): Fix function description
	comments.

	* semaphore.c (sem_post): Correct typo in comment.

Mon Jan 11 20:33:19 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.h: Re-arrange conditional compile of pthread_cleanup-*
	macros.

	* cleanup.c (ptw32_push_cleanup): Provide conditional 
	compile of cleanup->prev.

1999-01-11  Tor Lillqvist <tml at iki.fi>

	* condvar.c (pthread_cond_init): Invert logic when testing the
	return value from calloc().

Sat Jan  9 14:32:08 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h: Compile-time switch for CYGWIN derived environments
	to use CreateThread instead of _beginthreadex. Ditto for ExitThread.
	Patch provided by Anders Norlander  <anorland at hem2.passagen.se>.

Tue Jan  5 16:33:04 1999  Ross Johnson  <rpj at swan.canberra.edu.au>

	* cleanup.c (ptw32_pop_cleanup): Add C++ version of __try/__except
	block. Move trailing "}" out of #ifdef _WIN32 block left there by
	(rpj's) mistake.

	* private.c: Remove #include <errno.h> which is included by pthread.h.

1998-12-11  Ben Elliston  <bje at toilet.to.cygnus.com>

	* README: Update info about subscribing to the mailing list.

Mon Jan  4 11:23:40 1999  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* all: No code changes, just cleanup.
	- remove #if 0 /* Pre Bossom */ enclosed code.
	- Remove some redundant #includes.
	* pthread.h: Update implemented/unimplemented routines list.
	* Tag the bossom merge branch getting ready to merge back to main
	trunk.

Tue Dec 29 13:11:16 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h: Move the following struct definitions to pthread.h:
	pthread_t_, pthread_attr_t_, pthread_mutex_t_, pthread_mutex_t_,
	pthread_mutexattr_t_, pthread_key_t_, pthread_cond_t_,
	pthread_condattr_t_, pthread_once_t_.

	* pthread.h: Add "_" prefix to pthread_push_cleanup and 
	pthread_pop_cleanup internal routines, and associated struct and
	typedefs.

	* buildlib.bat: Add compile command for semaphore.c

	* pthread.def: Comment out pthread_atfork routine name. 
	Now unimplemented.

	* tsd.c (pthread_setspecific): Rename tkAssocCreate to
	ptw32_tkAssocCreate.
	(pthread_key_delete): Rename tkAssocDestroy to
	ptw32_tkAssocDestroy.

	* sync.c (pthread_join): Rename threadDestroy to ptw32_threadDestroy

	* sched.c (is_attr): attr is now **attr (was *attr), so add extra
	NULL pointer test.
	(pthread_attr_setschedparam): Increase redirection for attr which is
	now a **.
	(pthread_attr_getschedparam): Ditto.
	(pthread_setschedparam): Change thread validation and rename "thread"
 	Win32 thread Handle element name to match John Bossom's version.
	(pthread_getschedparam): Ditto.

	* private.c (ptw32_threadDestroy): Rename call to
	callUserDestroyRoutines() as ptw32_callUserDestroyRoutines()

	* misc.c: Add #include "implement.h".

	* dll.c: Remove defined(KLUDGE) wrapped code.

	* fork.c: Remove redefinition of ENOMEM.
	Remove pthread_atfork() and fork() with #if 0/#endif.

	* create.c (pthread_create): Rename threadStart and threadDestroy calls
	to ptw32_threadStart and ptw32_threadDestroy.

	* implement.h: Rename "detachedstate" to "detachstate".

	* attr.c: Rename "detachedstate" to "detachstate".

Mon Dec 28 09:54:39 1998  John Bossom

	* semaphore.c: Initial version.
	* semaphore.h: Initial version.

Mon Dec 28 09:54:39 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.h (pthread_attr_t_): Change to *pthread_attr_t.

Mon Dec 28 09:54:39 1998  John Bossom, Ben Elliston

	* attr.c (pthread_attr_setstacksize): Merge with John's version.
	(pthread_attr_getstacksize): Merge with John's version.
	(pthread_attr_setstackaddr): Merge with John's version.
	(pthread_attr_getstackaddr): Merge with John's version.
	(pthread_attr_init): Merge with John's version.
	(pthread_attr_destroy): Merge with John's version.
	(pthread_attr_getdetachstate): Merge with John's version.
	(pthread_attr_setdetachstate): Merge with John's version.
	(is_attr): attr is now **attr (was *attr), so add extra NULL pointer
	test.

Mon Dec 28 09:54:39 1998  Ross Johnson

	* implement.h (pthread_attr_t_): Add and rename elements in JEB's
	version to correspond to original, so that it can be used with
	original attr routines.

	* pthread.h: Add #endif at end which was truncated in merging.

Sun Dec 20 14:51:58 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* misc.c (pthreadCancelableWait): New function by John Bossom. Non-standard
	but provides a hook that can be used to implement cancellation points in
	applications that use this library.

	* pthread.h (pthread_cleanup_pop): C++ (non-WIN32) version uses
	try/catch to emulate John Bossom's WIN32 __try/__finally behaviour.
	In the WIN32 version __finally block, add a test for AbnormalTermination otherwise
	cleanup is only run if the cleanup_pop execute arg is non-zero. Cancellation
	should cause the cleanup to run irrespective of the execute arg.

	* condvar.c (pthread_condattr_init): Replaced by John Bossom's version.
	(pthread_condattr_destroy): Replaced by John Bossom's version.
	(pthread_condattr_getpshared): Replaced by John Bossom's version.
	(pthread_condattr_setpshared): Replaced by John Bossom's version.
	(pthread_cond_init): Replaced by John Bossom's version.
	Fix comment (refered to mutex rather than condition variable).
	(pthread_cond_destroy): Replaced by John Bossom's version.
	(pthread_cond_wait): Replaced by John Bossom's version.
	(pthread_cond_timedwait): Replaced by John Bossom's version.
	(pthread_cond_signal): Replaced by John Bossom's version.
	(pthread_cond_broadcast): Replaced by John Bossom's version.

Thu Dec 17 19:10:46 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* tsd.c (pthread_key_create): Replaced by John Bossom's version.
	(pthread_key_delete): Replaced by John Bossom's version.
	(pthread_setspecific): Replaced by John Bossom's version.
	(pthread_getspecific): Replaced by John Bossom's version.

Mon Dec  7 09:44:40 1998  John Bossom

	* cancel.c (pthread_setcancelstate): Replaced.
	(pthread_setcanceltype): Replaced.
	(pthread_testcancel): Replaced.
	(pthread_cancel): Replaced.
	
	* exit.c (pthread_exit): Replaced.

	* misc.c (pthread_self): Replaced.
	(pthread_equal): Replaced.

	* sync.c (pthread_detach): Replaced.
	(pthread_join): Replaced.

	* create.c (pthread_create): Replaced.

	* private.c (ptw32_processInitialize): New.
	(ptw32_processTerminate): New.
	(ptw32_threadStart): New.
 	(ptw32_threadDestroy): New.
	(ptw32_cleanupStack): New.
	(ptw32_tkAssocCreate): New.
	(ptw32_tkAssocDestroy): New.
	(ptw32_callUserDestroyRoutines): New.

	* implement.h: Added non-API structures and declarations.

	* dll.c (PthreadsEntryPoint): Cast return value of GetProcAddress
	to resolve compile warning from MSVC.

	* dll.c (DLLmain): Replaced.
	* dll.c (PthreadsEntryPoint):
	Re-applied Anders Norlander's patch:-
	Initialize ptw32_try_enter_critical_section at startup
	and release kernel32 handle when DLL is being unloaded.

Sun Dec  6 21:54:35 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* buildlib.bat: Fix args to CL when building the .DLL

	* cleanup.c (ptw32_destructor_run_all): Fix TSD key management.
	This is a tidy-up before TSD and Thread management is completely
	replaced by John Bossom's code.

	* tsd.c (pthread_key_create): Fix TSD key management.

	* global.c (ptw32_key_virgin_next): Initialise.

	* build.bat: New DOS script to compile and link a pthreads app
	using Microsoft's CL compiler linker.
	* buildlib.bat: New DOS script to compile all the object files
	and create pthread.lib and pthread.dll using Microsoft's CL
	compiler linker.

1998-12-05  Anders Norlander  <anorland at hem2.passagen.se>

	* implement.h (ptw32_try_enter_critical_section): New extern
	* dll.c (ptw32_try_enter_critical_section): New pointer to
	TryEnterCriticalSection if it exists; otherwise NULL.
	* dll.c (PthreadsEntryPoint):
	Initialize ptw32_try_enter_critical_section at startup
	and release kernel32 handle when DLL is being unloaded.
	* mutex.c (pthread_mutex_trylock): Replaced check for NT with
	a check if ptw32_try_enter_critical_section is valid
	pointer to a function. Call ptw32_try_enter_critical_section
	instead of TryEnterCriticalSection to avoid errors on Win95.

Thu Dec 3 13:32:00 1998  Ross Johnson  <rpj at ise.canberra.edu.au>

	* README: Correct cygwin32 compatibility statement.

Sun Nov 15 21:24:06 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* cleanup.c (ptw32_destructor_run_all): Declare missing void * arg.
	Fixup CVS merge conflicts.

1998-10-30  Ben Elliston  <bje at cygnus.com>

	* condvar.c (cond_wait): Fix semantic error. Test for equality
	instead of making an assignment.

Fri Oct 30 15:15:50 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* cleanup.c (ptw32_handler_push): Fixed bug appending new
	handler to list reported by Peter Slacik
	<Peter.Slacik at leibinger.freinet.de>.
	(new_thread): Rename poorly named local variable to
	"new_handler".

Sat Oct 24 18:34:59 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* global.c: Add TSD key management array and index declarations.

	* implement.h: Ditto for externs.

Fri Oct 23 00:08:09 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h  (PTW32_TSD_KEY_REUSE): Add enum.

	* private.c (ptw32_delete_thread): Add call to
	ptw32_destructor_run_all() to clean up the threads keys.

	* cleanup.c (ptw32_destructor_run_all): Check for no more dirty
	keys to run destructors on. Assume that the destructor call always
	succeeds and set the key value to NULL.

Thu Oct 22 21:44:44 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* tsd.c (pthread_setspecific): Add key management code.
	(pthread_key_create): Ditto.
	(pthread_key_delete): Ditto.

	* implement.h (struct ptw32_tsd_key): Add status member.

	* tsd.c: Add description of pthread_key_delete() from the
	standard as a comment.

Fri Oct 16 17:38:47 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* cleanup.c (ptw32_destructor_run_all): Fix and improve
	stepping through the key table.

Thu Oct 15 14:05:01 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* private.c (ptw32_new_thread): Remove init of destructorstack.
	No longer an element of pthread_t.

	* tsd.c (pthread_setspecific): Fix type declaration and cast.
	(pthread_getspecific): Ditto.
	(pthread_getspecific): Change error return value to NULL if key
	is not in use.

Thu Oct 15 11:53:21 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* global.c (ptw32_tsd_key_table): Fix declaration.

	* implement.h(ptw32_TSD_keys_TlsIndex): Add missing extern.
	(ptw32_tsd_mutex): Ditto.

	* create.c (ptw32_start_call): Fix "keys" array declaration.
	Add comment.

	* tsd.c (pthread_setspecific): Fix type declaration and cast.
	(pthread_getspecific): Ditto.

	* cleanup.c (ptw32_destructor_run_all): Declare missing loop
	counter.

Wed Oct 14 21:09:24 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c (ptw32_new_thread): Increment ptw32_threads_count.
	(ptw32_delete_thread): Decrement ptw32_threads_count.
	Remove some comments.

	* exit.c (ptw32_exit): : Fix two pthread_mutex_lock() calls that
 	should have been pthread_mutex_unlock() calls.
	(ptw32_vacuum): Remove call to ptw32_destructor_pop_all().

	* create.c (pthread_create): Fix two pthread_mutex_lock() calls that
 	should have been pthread_mutex_unlock() calls.

	* global.c (ptw32_tsd_mutex): Add mutex for TSD operations.

	* tsd.c (pthread_key_create): Add critical section.
	(pthread_setspecific): Ditto.
	(pthread_getspecific): Ditto.
	(pthread_key_delete): Ditto.

	* sync.c (pthread_join): Fix two pthread_mutex_lock() calls that
 	should have been pthread_mutex_unlock() calls.

Mon Oct 12 00:00:44 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h (ptw32_tsd_key_table): New.

	* create.c (ptw32_start_call): Initialise per-thread TSD keys
	to NULL.

	* misc.c (pthread_once): Correct typo in comment.

	* implement.h (ptw32_destructor_push): Remove.
	(ptw32_destructor_pop): Remove.
	(ptw32_destructor_run_all): Rename from ptw32_destructor_pop_all.
	 (PTW32_TSD_KEY_DELETED): Add enum.
	 (PTW32_TSD_KEY_INUSE): Add enum.

	* cleanup.c (ptw32_destructor_push): Remove.
	(ptw32_destructor_pop): Remove.
	(ptw32_destructor_run_all): Totally revamped TSD.

	* dll.c (ptw32_TSD_keys_TlsIndex): Initialise.

	* tsd.c (pthread_setspecific): Totally revamped TSD.
	(pthread_getspecific): Ditto.
	(pthread_create): Ditto.
	(pthread_delete): Ditto.

Sun Oct 11 22:44:55 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* global.c (ptw32_tsd_key_table): Add new global.

	* implement.h (ptw32_tsd_key_t and struct ptw32_tsd_key):
	Add.
	(struct _pthread): Remove destructorstack.

	* cleanup.c (ptw32_destructor_run_all): Rename from
 	ptw32_destructor_pop_all. The key destructor stack was made
 	global rather than per-thread. No longer removes destructor nodes
	from the stack. Comments updated.

1998-10-06  Ben Elliston  <bje at cygnus.com>

	* condvar.c (cond_wait): Use POSIX, not Win32 mutex calls.
	(pthread_cond_broadcast): Likewise.
	(pthread_cond_signal): Likewise.

1998-10-05  Ben Elliston  <bje at cygnus.com>

	* pthread.def: Update. Some functions aren't available yet, others
	are macros in <pthread.h>.

	* tests/join.c: Remove; useless.

Mon Oct  5 14:25:08 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* pthread.def: New file for building the DLL.

1998-10-05  Ben Elliston  <bje at cygnus.com>

	* misc.c (pthread_equal): Correct inverted logic bug.
	(pthread_once): Use the POSIX mutex primitives, not Win32. Remove
	irrelevant FIXME comment.

	* global.c (PTHREAD_MUTEX_INITIALIZER): Move to pthread.h.

	* pthread.h (PTHREAD_MUTEX_INITIALIZER): Define.
	(pthread_mutex_t): Reimplement as a struct containing a valid
	flag. If the flag is ever down upon entry to a mutex operation,
	we call pthread_mutex_create() to initialise the object. This
	fixes the problem of how to handle statically initialised objects
	that can't call InitializeCriticalSection() due to their context.
	(PTHREAD_ONCE_INIT): Define.

	* mutex.c (pthread_mutex_init): Set valid flag.
	(pthread_mutex_destroy): Clear valid flag.
	(pthread_mutex_lock): Check and handle the valid flag.
	(pthread_mutex_unlock): Likewise.
	(pthread_mutex_trylock): Likewise.

	* tests/mutex3.c: New file; test for the static initialisation
	macro. Passes.

	* tests/create1.c: New file; test pthread_create(). Passes.
	
	* tests/equal.c: Poor test; remove.
	
	* tests/equal1.c New file; test pthread_equal(). Passes.

	* tests/once1.c: New file; test for pthread_once(). Passes.

	* tests/self.c: Remove; rename to self1.c.

	* tests/self1.c: This is the old self.c.

	* tests/self2.c: New file. Test pthread_self() with a single
	thread. Passes.

	* tests/self3.c: New file. Test pthread_self() with a couple of
	threads to ensure their thread IDs differ. Passes.
	
1998-10-04  Ben Elliston  <bje at cygnus.com>

	* tests/mutex2.c: Test pthread_mutex_trylock(). Passes.

	* tests/mutex1.c: New basic test for mutex functions (it passes).
	(main): Eliminate warning.

	* configure.in: Test for __stdcall, not _stdcall. Typo.

	* configure: Regenerate.

	* attr.c (pthread_attr_setstackaddr): Remove FIXME comment. Win32
	does know about ENOSYS after all.
	(pthread_attr_setstackaddr): Likewise.

1998-10-03  Ben Elliston  <bje at cygnus.com>

	* configure.in: Test for the `_stdcall' keyword.  Define `STDCALL'
	to `_stdcall' if we have it, null otherwise.

	* configure: Regenerate.

	* acconfig.h (STDCALL): New define.

	* config.h.in: Regenerate.

	* create.c (ptw32_start_call): Add STDCALL prefix.
	
	* mutex.c (pthread_mutex_init): Correct function signature.

	* attr.c (pthread_attr_init): Only zero out the `sigmask' member
	if we have the sigset_t type.

	* pthread.h: No need to include <unistd.h>.  It doesn't even exist
	on Win32! Again, an artifact of cross-compilation.	
	(pthread_sigmask): Only provide if we have the sigset_t type.

	* process.h: Remove. This was a stand-in before we started doing
	native compilation under Win32.

	* pthread.h (pthread_mutex_init): Make `attr' argument const.

1998-10-02  Ben Elliston  <bje at cygnus.com>

	* COPYING: Remove.

	* COPYING.LIB: Add. This library is under the LGPL.

1998-09-13  Ben Elliston  <bje at cygnus.com>

	* configure.in: Test for required system features.

	* configure: Generate. 

	* acconfig.h: New file.

	* config.h.in: Generate.

	* Makefile.in: Renamed from Makefile.

	* COPYING: Import from a recent GNU package.

	* config.guess: Likewise.

	* config.sub: Likewise.

	* install-sh: Likewise.

	* config.h: Remove.  

	* Makefile: Likewise.

1998-09-12  Ben Elliston  <bje at cygnus.com>

	* windows.h: No longer needed; remove.

	* windows.c: Likewise.

Sat Sep 12 20:09:24 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* windows.h: Remove error number definitions. These are in <errno.h>
	
	* tsd.c: Add comment explaining rationale for not building
	POSIX TSD on top of Win32 TLS.

1998-09-12  Ben Elliston  <bje at cygnus.com>

	* {most}.c: Include <errno.h> to get POSIX error values.

	* signal.c (pthread_sigmask): Only provide if HAVE_SIGSET_T is
	defined.
 
	* config.h: #undef features, don't #define them.  This will be
	generated by autoconf very soon.
	
1998-08-11  Ben Elliston  <bje at cygnus.com>

	* Makefile (LIB): Define.
	(clean): Define target.
	(all): Build a library not just the object files.

	* pthread.h: Provide a definition for struct timespec if we don't
	already have one.

	* windows.c (TlsGetValue): Bug fix.
	
Thu Aug  6 15:19:22 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* misc.c (pthread_once): Fix arg 1 of EnterCriticalSection()
 	and LeaveCriticalSection() calls to pass address-of lock.

	* fork.c (pthread_atfork): Typecast (void (*)(void *)) funcptr
	in each ptw32_handler_push() call.

	* exit.c (ptw32_exit): Fix attr arg in 
	pthread_attr_getdetachstate() call.

	* private.c (ptw32_new_thread): Typecast (HANDLE) NULL.
	(ptw32_delete_thread): Ditto.

	* implement.h:  (PTW32_MAX_THREADS): Add define. This keeps
	changing in an attempt to make thread administration data types
	opaque and cleanup DLL startup.

	* dll.c (PthreadsEntryPoint): 
	(ptw32_virgins): Remove malloc() and free() calls.
	(ptw32_reuse): Ditto.
	(ptw32_win32handle_map): Ditto.
	(ptw32_threads_mutex_table): Ditto.

	* global.c (_POSIX_THREAD_THREADS_MAX): Initialise with 
	PTW32_MAX_THREADS.
	(ptw32_virgins): Ditto.
	(ptw32_reuse): Ditto.
	(ptw32_win32handle_map): Ditto.
	(ptw32_threads_mutex_table): Ditto.

	* create.c (pthread_create): Typecast (HANDLE) NULL.
	Typecast (unsigned (*)(void *)) start_routine.

	* condvar.c (pthread_cond_init): Add address-of operator & to
	arg 1 of pthread_mutex_init() call.
	(pthread_cond_destroy): Add address-of operator & to
	arg 1 of pthread_mutex_destroy() call. 

	* cleanup.c (ptw32_destructor_pop_all): Add (int) cast to 
	pthread_getspecific() arg.
	(ptw32_destructor_pop): Add (void *) cast to "if" conditional.
	(ptw32_destructor_push): Add (void *) cast to
	ptw32_handler_push() "key" arg.
	(malloc.h): Add include.

	* implement.h (ptw32_destructor_pop): Add prototype.

	* tsd.c (implement.h): Add include.

	* sync.c (pthread_join): Remove target_thread_mutex and it's
	initialisation. Rename getdetachedstate to getdetachstate.
	Remove unused variable "exitcode".
	(pthread_detach): Remove target_thread_mutex and it's
	initialisation. Rename getdetachedstate to getdetachstate.
	Rename setdetachedstate to setdetachstate.

	* signal.c (pthread_sigmask): Rename SIG_SET to SIG_SETMASK.
	Cast "set" to (long *) in assignment to passify compiler warning.
	Add address-of operator & to thread->attr.sigmask in memcpy() call
	and assignment.
	(pthread_sigmask): Add address-of operator & to thread->attr.sigmask
	in memcpy() call and assignment.

	* windows.h (THREAD_PRIORITY_ERROR_RETURN): Add.
	(THREAD_PRIORITY_LOWEST): Add.
	(THREAD_PRIORITY_HIGHEST): Add.

	* sched.c (is_attr): Add function.
	(implement.h): Add include.
	(pthread_setschedparam): Rename all instances of "sched_policy"
	to "sched_priority".
	(pthread_getschedparam): Ditto.

Tue Aug  4 16:57:58 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* private.c (ptw32_delete_thread): Fix typo. Add missing ';'.

	* global.c (ptw32_virgins): Change types from pointer to 
	array pointer.
	(ptw32_reuse): Ditto.
	(ptw32_win32handle_map): Ditto.
	(ptw32_threads_mutex_table): Ditto.

	* implement.h(ptw32_virgins): Change types from pointer to 
	array pointer.
	(ptw32_reuse): Ditto.
	(ptw32_win32handle_map): Ditto.
	(ptw32_threads_mutex_table): Ditto.

	* private.c (ptw32_delete_thread): Fix "entry" should be "thread".

	* misc.c (pthread_self): Add extern for ptw32_threadID_TlsIndex.

	* global.c: Add comment.

	* misc.c (pthread_once): Fix member -> dereferences.
	Change ptw32_once_flag to once_control->flag in "if" test.

Tue Aug  4 00:09:30 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h(ptw32_virgins): Add extern.
	(ptw32_virgin_next): Ditto.
	(ptw32_reuse): Ditto.
	(ptw32_reuse_top): Ditto.
	(ptw32_win32handle_map): Ditto.
	(ptw32_threads_mutex_table): Ditto.

	* global.c (ptw32_virgins): Changed from array to pointer.
	Storage allocation for the array moved into dll.c.
	(ptw32_reuse): Ditto.
	(ptw32_win32handle_map): Ditto.
	(ptw32_threads_mutex_table): Ditto.

	* dll.c (PthreadsEntryPoint): Set up thread admin storage when
	DLL is loaded.

	* fork.c (pthread_atfork): Fix function pointer arg to all
	ptw32_handler_push() calls. Change "arg" arg to NULL in child push.

	* exit.c: Add windows.h and process.h includes.
	(ptw32_exit): Add local detachstate declaration.
	(ptw32_exit): Fix incorrect name for pthread_attr_getdetachstate().

	* pthread.h (_POSIX_THREAD_ATTR_STACKSIZE): Move from global.c
	(_POSIX_THREAD_ATTR_STACKADDR): Ditto.

	* create.c (pthread_create): Fix #if should be #ifdef.
	(ptw32_start_call): Remove usused variables.

	* process.h: Create.

	* windows.h: Move _beginthreadex and _endthreadex into
	process.h

Mon Aug  3 21:19:57 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* condvar.c (pthread_cond_init): Add NULL attr to
	pthread_mutex_init() call - default attributes will be used.
	(cond_wait): Fix typo.
	(cond_wait): Fix typo - cv was ev.
	(pthread_cond_broadcast): Fix two identical typos.

	* cleanup.c (ptw32_destructor_pop_all): Remove _ prefix from
	PTHREAD_DESTRUCTOR_ITERATIONS.

	* pthread.h: Move _POSIX_* values into posix.h

	* pthread.h: Fix typo in pthread_mutex_init() prototype.

	* attr.c (pthread_attr_init): Fix error in priority member init.

	* windows.h (THREAD_PRIORITY_NORMAL): Add.

	* pthread.h (sched_param): Add missing ';' to struct definition. 

	* attr.c (pthread_attr_init): Remove obsolete pthread_attr_t
	member initialisation - cancelstate, canceltype, cancel_pending.
	(is_attr): Make arg "attr" a const.

	* implement.h  (PTW32_HANDLER_POP_LIFO): Remove definition.
	 (PTW32_HANDLER_POP_FIFO): Ditto.
	 (PTW32_VALID): Add missing newline escape (\).
	(ptw32_handler_node): Make element "next" a pointer.

1998-08-02  Ben Elliston  <bje at cygnus.com>

	* windows.h: Remove duplicate TlsSetValue() prototype.  Add 
	TlsGetValue() prototype.
	(FALSE): Define.
	(TRUE): Likewise.
	Add forgotten errno values.  Guard against multiple #includes.

	* windows.c: New file.  Implement stubs for Win32 functions.

	* Makefile (SRCS): Remove.  Not explicitly needed.
	(CFLAGS): Add -Wall for all warnings with GCC.

Sun Aug  2 19:03:42 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* config.h: Create. This is a temporary stand-in for autoconf yet
	to be done.
 	(HAVE_SIGNAL_H): Add.

	* pthread.h: Minor rearrangement for temporary config.h.

Fri Jul 31 14:00:29 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* cleanup.c (ptw32_destructor_pop): Implement. Removes
	destructors associated with a key without executing them.
	(ptw32_destructor_pop_all): Add FIXME comment.

	* tsd.c (pthread_key_delete): Add call to ptw32_destructor_pop().

Fri Jul 31 00:05:45 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* tsd.c (pthread_key_create): Update to properly associate
	the destructor routine with the key.
	(pthread_key_delete): Add FIXME comment.

	* exit.c (ptw32_vacuum): Add call to
	ptw32_destructor_pop_all().

	* implement.h (ptw32_handler_pop_all): Add prototype.
	(ptw32_destructor_pop_all): Ditto.

	* cleanup.c (ptw32_destructor_push): Implement. This is just a
	call to ptw32_handler_push().
	(ptw32_destructor_pop_all): Implement. This is significantly
	different to ptw32_handler_pop_all().

	* Makefile (SRCS): Create. Preliminary.

	* windows.h: Create. Contains Win32 definitions for compile
	testing. This is just a standin for the real one.

	* pthread.h (SIG_UNBLOCK): Fix typo. Was SIG_BLOCK.
	(windows.h): Add include. Required for CRITICAL_SECTION.
	(pthread_cond_t): Move enum declaration outside of struct
	definition.
	(unistd.h): Add include - may be temporary.

	* condvar.c (windows.h): Add include.

	* implement.h  (PTW32_THIS): Remove - no longer required.
	 (PTW32_STACK): Use pthread_self() instead of  PTW32_THIS.

Thu Jul 30 23:12:45 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h: Remove ptw32_find_entry() prototype.

	* private.c: Extend comments.
	Remove ptw32_find_entry() - no longer needed.

	* create.c (ptw32_start_call): Add call to TlsSetValue() to
	store the thread ID.

	* dll.c (PthreadsEntryPoint): Implement. This is called
	whenever a process loads the DLL. Used to initialise thread
	local storage.

	* implement.h: Add ptw32_threadID_TlsIndex.
	Add ()s around  PTW32_VALID expression.

	* misc.c (pthread_self): Re-implement using Win32 TLS to store
	the threads own ID.

Wed Jul 29 11:39:03 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c: Corrections in comments.
	(ptw32_new_thread): Alter "if" flow to be more natural.

	* cleanup.c (ptw32_handler_push): Same as below.

	* create.c (pthread_create): Same as below.

	* private.c (ptw32_new_thread): Rename "new" to "new_thread".
	Since when has a C programmer been required to know C++?

Tue Jul 28 14:04:29 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* implement.h: Add  PTW32_VALID macro.

	* sync.c (pthread_join): Modify to use the new thread
	type and ptw32_delete_thread(). Rename "target" to "thread".
	Remove extra local variable "target".
	(pthread_detach): Ditto.

	* signal.c (pthread_sigmask): Move init of "us" out of inner block.
	Fix instance of "this" should have been "us". Rename "us" to "thread".

	* sched.c (pthread_setschedparam): Modify to use the new thread
	type.
	(pthread_getschedparam): Ditto.

	* private.c (ptw32_find_thread): Fix return type and arg.

	* implement.h: Remove  PTW32_YES and  PTW32_NO.
	(ptw32_new_thread): Add prototype.
	(ptw32_find_thread): Ditto.
	(ptw32_delete_thread): Ditto.
	(ptw32_new_thread_entry): Remove prototype.
	(ptw32_find_thread_entry): Ditto.
	(ptw32_delete_thread_entry): Ditto.
	 (  PTW32_NEW,  PTW32_INUSE,  PTW32_EXITED,  PTW32_REUSE):
	Add.


	* create.c (pthread_create): Minor rename "us" to "new" (I need
	these cues but it doesn't stop me coming out with some major bugs
	at times).
	Load start_routine and arg into the thread so the wrapper can
	call it.

	* exit.c (pthread_exit): Fix pthread_this should be pthread_self.

	* cancel.c (pthread_setcancelstate): Change
 	ptw32_threads_thread_t * to pthread_t and init with
 	pthread_this().
	(pthread_setcanceltype): Ditto.

	* exit.c (ptw32_exit): Add new pthread_t arg.
	Rename ptw32_delete_thread_entry to ptw32_delete_thread.
	Rename "us" to "thread".
	(pthread_exit): Call ptw32_exit with added thread arg.

	* create.c (ptw32_start_call): Insert missing ")".
	Add "us" arg to ptw32_exit() call.
	(pthread_create): Modify to use new thread allocation scheme.

	* private.c: Added detailed explanation of the new thread
	allocation scheme.
	(ptw32_new_thread): Totally rewritten to use
	new thread allocation scheme.
	(ptw32_delete_thread): Ditto.
	(ptw32_find_thread): Obsolete.

Mon Jul 27 17:46:37 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* create.c (pthread_create): Start of rewrite. Not completed yet.

	* private.c (ptw32_new_thread_entry): Start of rewrite. Not
	complete.

	* implement.h (ptw32_threads_thread): Rename, remove thread
	member, add win32handle and ptstatus members.
	(ptw32_t): Add.

	* pthread.h: pthread_t is no longer mapped directly to a Win32
	HANDLE type. This is so we can let the Win32 thread terminate and
	reuse the HANDLE while pthreads holds it's own thread ID until
	the last waiting join exits.

Mon Jul 27 00:20:37 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c (ptw32_delete_thread_entry): Destroy the thread
 	entry attribute object before deleting the thread entry itself.

	* attr.c (pthread_attr_init): Initialise cancel_pending = FALSE.
	(pthread_attr_setdetachstate): Rename "detached" to "detachedstate".
	(pthread_attr_getdetachstate): Ditto.

	* exit.c (ptw32_exit): Fix incorrect check for detachedstate.

	* implement.h (ptw32_call_t): Remove env member. 

Sun Jul 26 13:06:12 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h (ptw32_new_thread_entry): Fix prototype.
	(ptw32_find_thread_entry): Ditto.
	(ptw32_delete_thread_entry): Ditto.
	(ptw32_exit): Add prototype.

	* exit.c (ptw32_exit): New function. Called from pthread_exit()
	and ptw32_start_call() to exit the thread. It allows an extra
	argument which is the return code passed to _endthreadex().
	(ptw32_exit): Move thread entry delete call from ptw32_vacuum()
	into here. Add more explanation of thread entry deletion.
	(ptw32_exit): Clarify comment.

	* create.c (ptw32_start_call): Change pthread_exit() call to
	ptw32_exit() call.

	* exit.c (ptw32_vacuum): Add thread entry deletion code
	moved from ptw32_start_call(). See next item.
	(pthread_exit): Remove longjmp(). Add mutex lock around thread table
	manipulation code. This routine now calls _enthreadex().

	* create.c (ptw32_start_call): Remove setjmp() call and move
	cleanup code out. Call pthread_exit(NULL) to terminate the thread.

1998-07-26  Ben Elliston  <bje at cygnus.com>

	* tsd.c (pthread_getspecific): Update comments.

	* mutex.c (pthread_mutexattr_setpshared): Not supported; remove.
	(pthread_mutexattr_getpshared): Likewise.

	* pthread.h (pthread_mutexattr_setpshared): Remove prototype.
	(pthread_mutexattr_getpshared): Likewise.

Sun Jul 26 00:09:59 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* sync.c: Rename all instances of ptw32_count_mutex to
	ptw32_table_mutex.

	* implement.h: Rename ptw32_count_mutex to
	ptw32_table_mutex.

	* global.c: Rename ptw32_count_mutex to
	ptw32_table_mutex.

	* create.c (pthread_create): Add critical sections.
	(ptw32_start_call): Rename ptw32_count_mutex to
	ptw32_table_mutex.

	* cancel.c (pthread_setcancelstate): Fix indirection bug and rename
	"this" to "us".

	* signal.c (pthread_sigmask): Rename "this" to "us" and fix some
	minor syntax errors. Declare "us" and initialise it.

	* sync.c (pthread_detach): Rename "this" to "target".

	* pthread.h: Converting PTHREAD_* defines to alias the (const int)
	values in global.c.

	* global.c: Started converting PTHREAD_* defines to (const int) as
 	a part of making the eventual pthreads DLL binary compatible
 	through version changes.

	* condvar.c (cond_wait): Add cancellation point. This applies the
	point to both pthread_cond_wait() and pthread_cond_timedwait().

	* exit.c (pthread_exit): Rename "this" to "us".

	* implement.h: Add comment.

	* sync.c (pthread_join): I've satisfied myself that pthread_detach()
	does set the detached attribute in the thread entry attributes
	to PTHREAD_CREATE_DETACHED. "if" conditions were changed to test
	that attribute instead of a separate flag.

	* create.c (pthread_create): Rename "this" to "us".
	(pthread_create): cancelstate and canceltype are not attributes
	so the copy to thread entry attribute storage was removed.
	Only the thread itself can change it's cancelstate or canceltype,
	ie. the thread must exist already.

	* private.c (ptw32_delete_thread_entry): Mutex locks removed.
	Mutexes must be applied at the caller level.
	(ptw32_new_thread_entry): Ditto.
	(ptw32_new_thread_entry): Init cancelstate, canceltype, and
	cancel_pending to default values.
	(ptw32_new_thread_entry): Rename "this" to "new".
	(ptw32_find_thread_entry): Rename "this" to "entry".
	(ptw32_delete_thread_entry): Rename "thread_entry" to "entry".

	* create.c (ptw32_start_call): Mutexes changed to
	ptw32_count_mutex. All access to the threads table entries is
	under the one mutex. Otherwise chaos reigns.

Sat Jul 25 23:16:51 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h (ptw32_threads_thread): Move cancelstate and
 	canceltype members out of pthread_attr_t into here.

	* fork.c (fork): Add comment.

1998-07-25  Ben Elliston  <bje at cygnus.com>

	* fork.c (fork): Autoconfiscate.

Sat Jul 25 00:00:13 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* create.c (ptw32_start_call): Set thread priority.  Ensure our
 	thread entry is removed from the thread table but only if
 	pthread_detach() was called and there are no waiting joins.
	(pthread_create): Set detach flag in thread entry if the 
	thread is created PTHREAD_CREATE_DETACHED.

	* pthread.h (pthread_attr_t): Rename member "detachedstate".

	* attr.c (pthread_attr_init): Rename attr members.

	* exit.c (pthread_exit): Fix indirection mistake.

	* implement.h  (PTW32_THREADS_TABLE_INDEX): Add.

	* exit.c (ptw32_vacuum): Fix incorrect args to
	ptw32_handler_pop_all() calls.
	Make thread entry removal conditional.

	* sync.c (pthread_join): Add multiple join and async detach handling.

	* implement.h  (PTW32_THREADS_TABLE_INDEX): Add.

	* global.c (ptw32_threads_mutex_table): Add.

	* implement.h (ptw32_once_flag): Remove.
	(ptw32_once_lock): Ditto.
	(ptw32_threads_mutex_table): Add.

	* global.c (ptw32_once_flag): Remove.
	(ptw32_once_lock): Ditto.

	* sync.c (pthread_join): Fix tests involving new return value
	from ptw32_find_thread_entry().
	(pthread_detach): Ditto.

	* private.c (ptw32_find_thread_entry): Failure return code
	changed from -1 to NULL.

Fri Jul 24 23:09:33 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* create.c (pthread_create): Change . to -> in sigmask memcpy() args.

	* pthread.h: (pthread_cancel): Add function prototype.
	(pthread_testcancel): Ditto.

1998-07-24  Ben Elliston  <bje at cygnus.com>

	* pthread.h (pthread_condattr_t): Rename dummy structure member.
	(pthread_mutexattr_t): Likewise.

Fri Jul 24 21:13:55 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* cancel.c (pthread_cancel): Implement.
	(pthread_testcancel): Implement.

	* exit.c (pthread_exit): Add comment explaining the longjmp().

	* implement.h (ptw32_threads_thread_t): New member cancelthread.
	 (PTW32_YES): Define.
	 (PTW32_NO): Define.
	(RND_SIZEOF): Remove.

	* create.c (pthread_create): Rename cancelability to cancelstate.

	* pthread.h (pthread_attr_t): Rename cancelability to cancelstate.
	(PTHREAD_CANCELED): Define.

1998-07-24  Ben Elliston  <bje at cygnus.com>

	* pthread.h (SIG_BLOCK): Define if not already defined.
	(SIG_UNBLOCK): Likewise.
	(SIG_SETMASK): Likewise.
	(pthread_attr_t): Add signal mask member.
	(pthread_sigmask): Add function prototype.

	* signal.c (pthread_sigmask): Implement.

	* create.c: #include <string.h> to get a prototype for memcpy().
	(pthread_create): New threads inherit their creator's signal
	mask.  Copy the signal mask to the new thread structure if we know
	about signals.
	
Fri Jul 24 16:33:17 1998  Ross Johnson  <rpj at swan.canberra.edu.au>

	* fork.c (pthread_atfork): Add all the necessary push calls.
	Local implementation semantics:
	If we get an ENOMEM at any time then ALL handlers
	(including those from previous pthread_atfork() calls) will be
	popped off each of the three atfork stacks before we return.
	(fork): Add all the necessary pop calls. Add the thread cancellation
	and join calls to the child fork.
	Add #includes.

	* implement.h: (ptw32_handler_push): Fix return type and stack arg
	type in prototype.
	(ptw32_handler_pop): Fix stack arg type in prototype.
	(ptw32_handler_pop_all): Fix stack arg type in prototype.

	* cleanup.c (ptw32_handler_push): Change return type to int and
	return ENOMEM if malloc() fails.

	* sync.c (pthread_detach): Use equality test, not assignment.

	* create.c (ptw32_start_call): Add call to Win32 CloseHandle()
	if thread is detached.

1998-07-24  Ben Elliston  <bje at cygnus.com>

	* sync.c (pthread_detach): Close the Win32 thread handle to
	emulate detached (or daemon) threads.

Fri Jul 24 03:00:25 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* sync.c (pthread_join): Save valueptr arg in joinvalueptr for
	pthread_exit() to use.

	* private.c (ptw32_new_thread_entry): Initialise joinvalueptr to
	NULL.

	* create.c (ptw32_start_call): Rewrite to facilitate joins.
	pthread_exit() will do a longjmp() back to here. Does appropriate
	cleanup and exit/return from the thread.
	(pthread_create): _beginthreadex() now passes a pointer to our
	thread table entry instead of just the call member of that entry.

	* implement.h (ptw32_threads_thread): New member 
	void ** joinvalueptr.
	(ptw32_call_t): New member jmpbuf env.

	* exit.c (pthread_exit): Major rewrite to handle joins and handing
	value pointer to joining thread. Uses longjmp() back to 
	ptw32_start_call().

	* create.c (pthread_create): Ensure values of new attribute members
	are copied to the thread attribute object.

	* attr.c (pthread_attr_destroy):  Fix merge conflicts.
	(pthread_attr_getdetachstate):  Fix merge conflicts.
	(pthread_attr_setdetachstate):  Fix merge conflicts.

	* pthread.h:  Fix merge conflicts.

	* sync.c (pthread_join): Fix merge conflicts.

Fri Jul 24 00:21:21 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* sync.c (pthread_join): Add check for valid and joinable
	thread.
	(pthread_detach): Implement. After checking for a valid and joinable
	thread, it's still a no-op.

	* private.c (ptw32_find_thread_entry): Bug prevented returning
	an error value in some cases.

	* attr.c (pthread_attr_setdetachedstate): Implement.
	(pthread_attr_getdetachedstate): Implement.

	* implement.h: Move more hidden definitions into here from
	pthread.h.

1998-07-24  Ben Elliston  <bje at cygnus.com>

	* pthread.h (PTHREAD_CREATE_JOINABLE): Define.
	(PTHREAD_CREATE_DETACHED): Likewise.
	(pthread_attr_t): Add new structure member `detached'.
	(pthread_attr_getdetachstate): Add function prototype.
	(pthread_attr_setdetachstate): Likewise.

	* sync.c (pthread_join): Return if the target thread is detached.

	* attr.c (pthread_attr_init): Initialise cancelability and
	canceltype structure members.
	(pthread_attr_getdetachstate): Implement.
	(pthread_attr_setdetachstate): Likewise.

	* implement.h  (PTW32_CANCEL_DEFAULTS): Remove.  Bit fields
	proved to be too cumbersome.  Set the defaults in attr.c using the
	public PTHREAD_CANCEL_* constants.

	* cancel.c: New file.

	* pthread.h (sched_param): Define this type.
	(pthread_attr_getschedparam): Add function prototype.
	(pthread_attr_setschedparam): Likewise.
	(pthread_setcancelstate): Likewise.
	(pthread_setcanceltype): Likewise.
	(sched_get_priority_min): Likewise.
	(sched_get_priority_max): Likewise.
	(pthread_mutexattr_setprotocol): Remove; not supported.
	(pthread_mutexattr_getprotocol): Likewise.
	(pthread_mutexattr_setprioceiling): Likewise.
	(pthread_mutexattr_getprioceiling): Likewise.
	(pthread_attr_t): Add canceltype member.  Update comments.
	(SCHED_OTHER): Define this scheduling policy constant.
	(SCHED_FIFO): Likewise.
	(SCHED_RR): Likewise.
	(SCHED_MIN): Define the lowest possible value for this constant.
	(SCHED_MAX): Likewise, the maximum possible value.
	(PTHREAD_CANCEL_ASYNCHRONOUS): Redefine.
	(PTHREAD_CANCEL_DEFERRED): Likewise.
	
	* sched.c: New file.
	(pthread_setschedparam): Implement.
	(pthread_getschedparam): Implement.
	(sched_get_priority_max): Validate policy argument.
	(sched_get_priority_min): Likewise.

	* mutex.c (pthread_mutexattr_setprotocol): Remove; not supported.
	(pthread_mutexattr_getprotocol): Likewise.
	(pthread_mutexattr_setprioceiling): Likewise.
	(pthread_mutexattr_getprioceiling): Likewise.

Fri Jul 24 00:21:21 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* create.c (pthread_create): Arg to ptw32_new_thread_entry()
	changed. See next entry. Move mutex locks out. Changes made yesterday
	and today allow us to start the new thread running rather than
	temporarily suspended.

	* private.c (ptw32_new_thread_entry): ptw32_thread_table
	was changed back to a table of thread structures rather than pointers.
	As such we're trading storage for increaded speed. This routine
	was modified to work with the new table. Mutex lock put in around
	global data accesses.
	(ptw32_find_thread_entry): Ditto
	(ptw32_delete_thread_entry): Ditto

Thu Jul 23 23:25:30 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* global.c: New. Global data objects declared here. These moved from
	pthread.h.

	* pthread.h: Move implementation hidden definitions into
	implement.h.

	* implement.h: Move implementation hidden definitions from
	pthread.h. Add constants to index into the different handler stacks.

	* cleanup.c (ptw32_handler_push): Simplify args. Restructure.
	(ptw32_handler_pop): Simplify args. Restructure.
	(ptw32_handler_pop_all): Simplify args. Restructure.

Wed Jul 22 00:16:22 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* attr.c, implement.h, pthread.h, ChangeLog: Resolve CVS merge
	conflicts.

	* private.c (ptw32_find_thread_entry): Changes to return type
	to support leaner ptw32_threads_table[] which now only stores
	ptw32_thread_thread_t *.
	(ptw32_new_thread_entry): Internal changes.
	(ptw32_delete_thread_entry): Internal changes to avoid contention.
 	Calling routines changed accordingly.

	* pthread.h: Modified cleanup macros to use new generic push and pop.
	Added destructor and atfork stacks to ptw32_threads_thread_t.

	* cleanup.c (ptw32_handler_push, ptw32_handler_pop,
	ptw32_handler_pop_all): Renamed cleanup push and pop routines
	and made generic to handle destructors and atfork handlers as
	well.

	* create.c (ptw32_start_call): New function is a wrapper for
	all new threads. It allows us to do some cleanup when the thread
	returns, ie. that is otherwise only done if the thread is cancelled.

	* exit.c (ptw32_vacuum): New function contains code from 
	pthread_exit() that we need in the new ptw32_start_call()
	as well.

	* implement.h: Various additions and minor changes.

	* pthread.h: Various additions and minor changes.
	Change cleanup handler macros to use generic handler push and pop
	functions.

	* attr.c: Minor mods to all functions.
	(is_attr): Implemented missing function.

	* create.c (pthread_create): More clean up.

	* private.c (ptw32_find_thread_entry): Implement.
	(ptw32_delete_thread_entry): Implement.
	(ptw32_new_thread_entry): Implement.
	These functions manipulate the implementations internal thread
	table and are part of general code cleanup and modularisation.
	They replace ptw32_getthreadindex() which was removed.

	* exit.c (pthread_exit): Changed to use the new code above.

	* pthread.h: Add cancelability constants. Update comments.

1998-07-22  Ben Elliston  <bje at cygnus.com>

	* attr.c (pthread_setstacksize): Update test of attr argument.
	(pthread_getstacksize): Likewise.
	(pthread_setstackaddr): Likewise.
	(pthread_getstackaddr): Likewise.
	(pthread_attr_init): No need to allocate any storage.
	(pthread_attr_destroy): No need to free any storage.

	* mutex.c (is_attr): Not likely to be needed; remove.
	(remove_attr): Likewise.
	(insert_attr): Likewise.

	* implement.h (ptw32_mutexattr_t): Moved to a public definition
	in pthread.h.  There was little gain in hiding these details.
	(ptw32_condattr_t): Likewise.
	(ptw32_attr_t): Likewise.

	* pthread.h (pthread_atfork): Add function prototype.
	(pthread_attr_t): Moved here from implement.h.

	* fork.c (pthread_atfork): Preliminary implementation.
	(ptw32_fork): Likewise.

Wed Jul 22 00:16:22 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* cleanup.c (ptw32_cleanup_push): Implement.
	(ptw32_cleanup_pop): Implement.
	(ptw32_do_cancellation): Implement.
	These are private to the implementation. The real cleanup functions
	are macros. See below.

	* pthread.h (pthread_cleanup_push): Implement as a macro.
	(pthread_cleanup_pop): Implement as a macro.
	Because these are macros which start and end a block, the POSIX scoping
	requirement is observed. See the comment in the file.

	* exit.c (pthread_exit): Refine the code.

	* create.c (pthread_create): Code cleanup.

	* implement.h (RND_SIZEOF): Add RND_SIZEOF(T) to round sizeof(T)
	up to multiple of DWORD.
	Add function prototypes.

	* private.c (ptw32_getthreadindex): "*thread" should have been 
	"thread". Detect empty slot fail condition.

1998-07-20  Ben Elliston  <bje at cygnus.com>

	* misc.c (pthread_once): Implement.  Don't use a per-application
	flag and mutex--make `pthread_once_t' contain these elements in
	their structure.  The earlier version had incorrect semantics.
	
	* pthread.h (ptw32_once_flag): Add new variable.  Remove.
	(ptw32_once_lock): Add new mutex lock to ensure integrity of
	access to ptw32_once_flag.  Remove.
	(pthread_once): Add function prototype.
	(pthread_once_t): Define this type.
	
Mon Jul 20 02:31:05 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* private.c (ptw32_getthreadindex): Implement.

	* pthread.h: Add application static data dependent on
	_PTHREADS_BUILD_DLL define. This is needed to avoid allocating
	non-sharable static data within the pthread DLL.

	* implement.h: Add ptw32_cleanup_stack_t, ptw32_cleanup_node_t
	and  PTW32_HASH_INDEX.

	* exit.c (pthread_exit): Begin work on cleanup and de-allocate
	thread-private storage.

	* create.c (pthread_create): Add thread to thread table.
	Keep a thread-private copy of the attributes with default values
	filled in when necessary. Same for the cleanup stack. Make 
	pthread_create C run-time library friendly by using _beginthreadex()
	instead of CreateThread(). Fix error returns.

Sun Jul 19 16:26:23 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h: Rename pthreads_thread_count to ptw32_threads_count.
	Create ptw32_threads_thread_t struct to keep thread specific data.

	* create.c: Rename pthreads_thread_count to ptw32_threads_count.
	(pthread_create): Handle errors from CreateThread().

1998-07-19  Ben Elliston  <bje at cygnus.com>

	* condvar.c (pthread_cond_wait): Generalise.  Moved from here ..
	(cond_wait): To here.
	(pthread_cond_timedwait): Implement; use generalised cond_wait().

	* pthread.h (pthread_key_t): Define this type.
	(pthread_key_create): Add function prototype.
	(pthread_setspecific): Likewise.
	(pthread_getspecific): Likwise.
	(pthread_key_delete): Likewise.

	* tsd.c (pthread_key_create): Implement.
	(pthread_setspecific): Likewise.
	(pthread_getspecific): Likewise.
	(pthread_key_delete): Likewise.

	* mutex.c (pthread_mutex_trylock): Return ENOSYS if this function
	is called on a Win32 platform which is not Windows NT.

1998-07-18  Ben Elliston  <bje at cygnus.com>

	* condvar.c (pthread_condattr_init): Do not attempt to malloc any
	storage; none is needed now that condattr_t is an empty struct.
	(pthread_condattr_destory): Likewise; do not free storage.
	(pthread_condattr_setpshared): No longer supported; return ENOSYS.
	(pthread_condattr_getpshared): Likewise.
	(pthread_cond_init): Implement with help from Douglas Schmidt.
	Remember to initialise the cv's internal mutex.
	(pthread_cond_wait): Likewise.
	(pthread_cond_signal): Likewise.
	(pthread_cond_broadcast): Likewise.
	(pthread_cond_timedwait): Preliminary implementation, but I need
	to see some API documentation for `WaitForMultipleObject'.
	(pthread_destory): Implement.

	* pthread.h (pthread_cond_init): Add function protoype.
	(pthread_cond_broadcast): Likewise.
	(pthread_cond_signal): Likewise.
	(pthread_cond_timedwait): Likewise.
	(pthread_cond_wait): Likewise.
	(pthread_cond_destroy): Likewise.
	(pthread_cond_t): Define this type.  Fix for u_int.  Do not assume
	that the mutex contained withing the pthread_cond_t structure will
	be a critical section.  Use our new POSIX type!

	* implement.h (ptw32_condattr_t): Remove shared attribute.

1998-07-17  Ben Elliston  <bje at cygnus.com>

	* pthread.h (PTHREADS_PROCESS_PRIVATE): Remove.
	(PTHREAD_PROCESS_SHARED): Likewise.  No support for mutexes shared
	across processes for now.
	(pthread_mutex_t): Use a Win32 CRITICAL_SECTION type for better
	performance.
	
	* implement.h (ptw32_mutexattr_t): Remove shared attribute.
	
	* mutex.c (pthread_mutexattr_setpshared): This optional function
	is no longer supported, since we want to implement POSIX mutex
	variables using the much more efficient Win32 critical section
	primitives.  Critical section objects in Win32 cannot be shared
	between processes.
	(pthread_mutexattr_getpshared): Likewise.
	(pthread_mutexattr_init): No need to malloc any storage; the
	attributes structure is now empty.
	(pthread_mutexattr_destroy): This is now a nop.
	(pthread_mutex_init): Use InitializeCriticalSection().
	(pthread_mutex_destroy): Use DeleteCriticalSection().
	(pthread_mutex_lock): Use EnterCriticalSection().
	(pthread_mutex_trylock): Use TryEnterCriticalSection().  This is
	not supported by Windows 9x, but trylock is a hack anyway, IMHO.
	(pthread_mutex_unlock): Use LeaveCriticalSection().

1998-07-14  Ben Elliston  <bje at cygnus.com>

	* attr.c (pthread_attr_setstacksize): Implement.
	(pthread_attr_getstacksize): Likewise.
	(pthread_attr_setstackaddr): Likewise.
	(pthread_attr_getstackaddr): Likewise.
	(pthread_attr_init): Likewise.
	(pthread_attr_destroy): Likewise.
	
	* condvar.c (pthread_condattr_init): Add `_cond' to function name.

	* mutex.c (pthread_mutex_lock): Add `_mutex' to function name.
	(pthread_mutex_trylock): Likewise.
	(pthread_mutex_unlock): Likewise.

	* pthread.h (pthread_condattr_setpshared): Fix typo.
	(pthread_attr_init): Add function prototype.
	(pthread_attr_destroy): Likewise.
	(pthread_attr_setstacksize): Likewise.
	(pthread_attr_getstacksize): Likewise.
	(pthread_attr_setstackaddr): Likewise.
	(pthread_attr_getstackaddr): Likewise.
	
Mon Jul 13 01:09:55 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h: Wrap in #ifndef _IMPLEMENT_H

	* create.c (pthread_create): Map stacksize attr to Win32.

	* mutex.c: Include implement.h

1998-07-13  Ben Elliston  <bje at cygnus.com>

	* condvar.c (pthread_condattr_init): Implement.
	(pthread_condattr_destroy): Likewise.
	(pthread_condattr_setpshared): Likewise.
	(pthread_condattr_getpshared): Likewise.
	
	* implement.h (PTHREAD_THREADS_MAX): Remove trailing semicolon.
	(PTHREAD_STACK_MIN): Specify; needs confirming.
	(ptw32_attr_t): Define this type.
	(ptw32_condattr_t): Likewise.

	* pthread.h (pthread_mutex_t): Define this type.
	(pthread_condattr_t): Likewise.
	(pthread_mutex_destroy): Add function prototype.
	(pthread_lock): Likewise.
	(pthread_trylock): Likewise.
	(pthread_unlock): Likewise.
	(pthread_condattr_init): Likewise.
	(pthread_condattr_destroy): Likewise.
	(pthread_condattr_setpshared): Likewise.
	(pthread_condattr_getpshared): Likewise.

	* mutex.c (pthread_mutex_init): Implement.
	(pthread_mutex_destroy): Likewise.
	(pthread_lock): Likewise.
	(pthread_trylock): Likewise.
	(pthread_unlock): Likewise.

1998-07-12  Ben Elliston  <bje at cygnus.com>

	* implement.h (ptw32_mutexattr_t): Define this implementation
	internal type.  Application programmers only see a mutex attribute
	object as a void pointer.

	* pthread.h (pthread_mutexattr_t): Define this type.
	(pthread_mutexattr_init): Add function prototype.
	(pthread_mutexattr_destroy): Likewise.
	(pthread_mutexattr_setpshared): Likewise.
	(pthread_mutexattr_getpshared): Likewise.
	(pthread_mutexattr_setprotocol): Likewise.
	(pthread_mutexattr_getprotocol): Likewise.
	(pthread_mutexattr_setprioceiling): Likewise.
	(pthread_mutexattr_getprioceiling): Likewise.
	(PTHREAD_PROCESS_PRIVATE): Define.
	(PTHREAD_PROCESS_SHARED): Define.

	* mutex.c (pthread_mutexattr_init): Implement.
	(pthread_mutexattr_destroy): Implement.
	(pthread_mutexattr_setprotocol): Implement.
	(pthread_mutexattr_getprotocol): Likewise.
	(pthread_mutexattr_setprioceiling): Likewise.
	(pthread_mutexattr_getprioceiling): Likewise.
	(pthread_mutexattr_setpshared): Likewise.
	(pthread_mutexattr_getpshared): Likewise.
	(insert_attr): New function; very preliminary implementation!
	(is_attr): Likewise.
	(remove_attr): Likewise.
	
Sat Jul 11 14:48:54 1998  Ross Johnson  <rpj at ixobrychus.canberra.edu.au>

	* implement.h: Preliminary implementation specific defines.

	* create.c (pthread_create): Preliminary implementation.

1998-07-11  Ben Elliston  <bje at cygnus.com>

	* sync.c (pthread_join): Implement.

	* misc.c (pthread_equal): Likewise.
	
	* pthread.h (pthread_join): Add function prototype.
	(pthread_equal): Likewise.
	
1998-07-10  Ben Elliston  <bje at cygnus.com>

	* misc.c (pthread_self): Implement.

	* exit.c (pthread_exit): Implement.

	* pthread.h (pthread_exit): Add function prototype.
	(pthread_self): Likewise.
	(pthread_t): Define this type.

1998-07-09  Ben Elliston  <bje at cygnus.com>

	* create.c (pthread_create): A dummy stub right now.

	* pthread.h (pthread_create): Add function prototype.
