project(IOKitTools)

add_compile_options(
	-Wno-error=int-conversion
)

add_darling_executable(ioreg ioreg.tproj/ioreg.c)
add_darling_executable(ioclasscount ioclasscount.tproj/ioclasscount.c)
add_darling_executable(ioalloccount ioalloccount.tproj/ioalloccount.c)

target_link_libraries(ioreg IOKit CoreFoundation ncurses)
target_link_libraries(ioclasscount IOKit CoreFoundation CoreSymbolication)
target_link_libraries(ioalloccount IOKit CoreFoundation CoreSymbolication)

install(TARGETS
	ioreg
	ioclasscount
	ioalloccount

	DESTINATION libexec/darling/usr/sbin)

install(FILES
	ioreg.tproj/ioreg.8
	ioclasscount.tproj/ioclasscount.8
	ioalloccount.tproj/ioalloccount.8

	DESTINATION libexec/darling/usr/share/man/man8)
