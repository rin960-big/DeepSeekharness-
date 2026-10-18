# DeepSeekharness-
DeepSeekharness权限提醒弹窗，这段代码会让你的DeepSeek harness在弹出权限请求时以最优先级弹出，让人一眼看到DeepSeek harness
install——》PowerShell：cd "F:\Paper shift\dsh-focus-on-approval"
powershell -NoProfile -ExecutionPolicy Bypass -File .\install.ps1
uninstall——》PowerShell：cd "F:\Paper shift\dsh-focus-on-approval"
powershell -NoProfile -ExecutionPolicy Bypass -File .\uninstall.ps1

working principle：The plugin runs inside the DSH Host process and listens to DSH’s session/event; when approval/asked occurs, it first calls ShowWindow(SW_RESTORE) if the window is minimized, then calls SetWindowPos(HWND_TOPMOST) to bring the window above all other windows, and optionally simulates a single Alt keypress followed by SetForegroundWindow so that the approval panel directly receives keyboard focus. After approval/decided occurs, it cancels the temporary topmost setting and restores the normal window z-order; multiple concurrent approvals are handled with a counter, and the topmost setting is canceled only after the last approval ends. It does not modify app.asar but only modifies the profile under the user directory, so DSH upgrades will not overwrite it.
