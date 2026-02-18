---
title: "Planning Ahead"
date: 2025-12-15
comments: true
tags: roadmap
---

It's common to recapitulate the past year as it ends, but let's do something
different and, instead of looking back at the record 6 releases we made in
2025 (it helps to introduce some bugs in them, so as to require making bug fix
releases soon after, but they still count), let's see what is coming in 2026.

First of all, we are going to release 3.3.2 relatively soon, maybe in January
but hopefully not later than February. This release will bring a few new
features that are already implemented in master (and are eagerly awaiting being
tested, so if you're interested in using them, please consider checking them
out even before this release):

- There is the new [wxStyledTextCtrlMiniMap][] class, which implements a small
  map, showing a scaled-down overview of the document being edited in the main
  `wxStyledTextCtrl` and automatically synchronized with it. It is very simple
  to use, as it's usually enough to just create it, see the updated `stc`
  sample for an example showing it, so there is not much to say about it, but
  it should be appreciated by the users. Thanks to [GIANTS Software][] for the
  grant which allowed us to develop this feature!

- Another new UI feature is the support for minimizing panes in wxAUI into
  taskbar-like docking bars. This is, again, very simple to use from the
  application point of view, as it's enough to just call [MinimizeButton]()
  function of `wxAuiPaneInfo` class when creating the pane to enable it and
  everything else is handled automatically by wxAUI. However there are some
  customization options available already and we will probably add more of them
  before final 3.3.2 release, so please let us know what else would you like to
  be able to change.

- And the final relatively important recently implemented feature has nothing
  to do with the UI: it's the possibility to choose between GLX and EGL-based
  implementations of `wxGLCanvas` in wxGTK. Previously this choice had to be
  done at compile-time, meaning that applications were forced to use EGL, even
  when using X11 GTK backend, where using GLX would be possible. Now it is
  possible to call [PreferGLX][] function to do it in this case.

- Of course, there were many other improvements and bug fixes since 3.3.1, in
  particular it is worth mentioning that all the third party libraries bundled
  with wxWidgets have been updated to their latest versions (thanks Maarten!),
  many bugs were fixed when using RTL writing direction (thanks Ali!), a few
  more classes were implemented in wxiOS (thanks Robert!) and `wxStaticText`
  has finally learnt how to wrap its contents automatically.

[wxStyledTextCtrlMiniMap]: https://docs.wxwidgets.org/latest/classwx_styled_text_ctrl_mini_map.html
[GIANTS Software]: https://giants-software.com/
[MinimizeButton]: https://docs.wxwidgets.org/latest/classwx_aui_pane_info.html#a99aee8968a56af51780f78bcc4752cc8
[PreferGLX]: https://docs.wxwidgets.org/latest/classwx_g_l_canvas.html#a9ee74808371cb6d2b98767cb5fbedd21


After 3.3.2 we will start thinking about making 3.4.0 release, which will be
the first stable release with [dark mode][] support for Windows. Right now it
looks like we may not even need a 3.3.3 before it, as no other major changes
are currently planned, but this may, of course, change depending on the
feedback we get after 3.3.2 release.

[dark mode]: https://wxwidgets.org/blog/2024/10/hello-darkness/

One thing that we unfortunately almost surely still won't have in 3.4.0 is GTK
4 support in wxGTK. This is something that will become more and more necessary
with time passing, of course, but upgrading from GTK 3 to GTK 4 is a major
endeavour and we're still looking for volunteers and/or grants to make it
happen. But surely if we wait for long enough, we'll just be able to ask an LLM
to write wxGTK4 for us, right?

Let me close this forecast for 2026 on this optimistic note. Happy holidays and
let's all hope for a better next year, and not just for wxWidgets!
