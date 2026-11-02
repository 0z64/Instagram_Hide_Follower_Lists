# Hide Follower & Following Lists

A small Python script that requests Instagram's `hide_followers_following_list` account setting be enabled for the account associated with your session. It uses an unofficial Instagram endpoint, so it may stop working or the setting may not be available for your account. It does not guarantee that your lists will be hidden from everyone; check the result in Instagram.

## Requirements

- Python 3 (standard library only; no packages to install)
- Your own Instagram `sessionid` cookie value for the account you want to update
- An internet connection

## Usage

From this directory, run:

```bash
python3 hide_lists.py
```

When prompted, enter **only the value** of your own `sessionid` cookie, not `sessionid=` or an entire cookie header. The input is hidden while you type. The script makes one request to `https://i.instagram.com/graphql/query` and prints `Enabled: Instagram returned value=true.` only if Instagram's response confirms the setting was enabled. Otherwise, it prints an error and exits with a nonzero status. It does not retry automatically.

## Security and limitations

- A session cookie grants access to your account. Never share it, paste it into an issue, commit it, or use someone else's cookie. If you believe it was exposed, sign out of affected sessions in Instagram and secure your account.
- The script sends your cookie to Instagram to authenticate the request. It does not save the cookie to a file. Redirects and environment-configured proxies are disabled for this request.
- This is not an official Instagram tool. Instagram may reject the request, change the endpoint, or restrict availability of the setting without notice.
- If the request times out or is interrupted, the change **may already have been applied**. Check the setting in Instagram before trying again.
- This script only requests that the setting be enabled; it does not include a way to disable it.
