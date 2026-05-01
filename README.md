# Bitcoin Node Dashboard

![License](https://img.shields.io/badge/license-MIT-green)
![Shell](https://img.shields.io/badge/shell-bash-green.svg)
![Platform](https://img.shields.io/badge/platform-Raspberry%20Pi%20%7C%20Linux-lightgrey.svg)

A terminal dashboard for monitoring a Bitcoin full node on Raspberry Pi. Displays host stats, resource usage, blockchain sync status, peer count and mempool info.

## Included Script
`dashboard.sh` prints the terminal dashboard.

![Dashboard output](assets/output.png)

## Installation

**Prerequisites** — the script requires `jq`, `bc`, and `curl`:
```bash
sudo apt install -y jq bc curl
```

**1. Clone the repository**
```bash
git clone https://github.com/janrothen/bitcoin-node-dashboard.git ~/bitcoin-node-dashboard
```

**2. Make the script executable**
```bash
chmod +x ~/bitcoin-node-dashboard/dashboard.sh
```

**3. Run it**
```bash
~/bitcoin-node-dashboard/dashboard.sh
```

**Optional: run on login**

Add the following line to `~/.bashrc` (or `~/.bash_profile`) to display the dashboard every time you open a shell (adjust the path accordingly):
```bash
echo '~/bitcoin-node-dashboard/dashboard.sh' >> ~/.bashrc
```

## Troubleshooting

| Problem | Likely cause | Fix |
|---|---|---|
| `jq: command not found` | `jq` not installed | `sudo apt install -y jq` |
| `bc: command not found` | `bc` not installed | `sudo apt install -y bc` |
| `curl: (7) Failed to connect` | Bitcoin RPC not reachable | Check that `bitcoind` is running and RPC credentials in the script are correct |
| Blockchain sync shows 0% | Node still starting up | Wait a minute and re-run; `bitcoind` may not be fully initialised |
| Dashboard shows stale data | Script exited early | Run manually to see the full error output: `bash -x ~/bitcoin-node-dashboard/dashboard.sh` |

## Contributing

Found a bug or have an idea? Open an issue or send a PR.

## License

MIT © Jan Rothen — see [LICENSE](LICENSE) for details.
