plugin_LTLIBRARIES = libgstmpg123.la

libgstmpg123_la_SOURCES = gstmpg123audiodec.c
libgstmpg123_la_CFLAGS = -DGST_USE_UNSTABLE_API \
	$(GST_PLUGINS_BASE_CFLAGS) \
	$(GST_BASE_CFLAGS) $(GST_CFLAGS) $(MPG123_CFLAGS)
libgstmpg123_la_LIBADD = $(GST_PLUGINS_BASE_LIBS) -lgstaudio-@GST_API_VERSION@ \
	$(GST_BASE_LIBS) $(GST_LIBS) $(MPG123_LIBS)
libgstmpg123_la_LDFLAGS = $(GST_PLUGIN_LDFLAGS)
libgstmpg123_la_LIBTOOLFLAGS = $(GST_PLUGIN_LIBTOOLFLAGS)

noinst_HEADERS = gstmpg123audiodec.h

Android.mk: Makefile.am $(BUILT_SOURCES)
	androgenizer \
	-:PROJECT libgstmpg123 -:SHARED libgstmpg123 \
	 -:TAGS eng debug \
         -:REL_TOP $(top_srcdir) -:ABS_TOP $(abs_top_srcdir) \
	 -:SOURCES $(libgstmpg123_la_SOURCES) \
	 -:CPPFLAGS $(CPPFLAGS) \
	 -:CFLAGS $(DEFS) $(DEFAULT_INCLUDES) $(libgstmpg123_la_CFLAGS) \
	 -:LDFLAGS $(libgstmpg123_la_LDFLAGS) \
	           $(libgstmpg123_la_LIBADD) \
	           -ldl \
	 -:PASSTHROUGH LOCAL_ARM_MODE:=arm \
		       LOCAL_MODULE_PATH:='$$(TARGET_OUT)/lib/gstreamer-@GST_API_VERSION@' \
	> $@
