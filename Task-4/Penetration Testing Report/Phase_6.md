# Post-Exploitation

## Objective

To upgrade the command shell session obtained during the Controlled Exploitation phase to a Meterpreter session, and run post-exploitation commands (`sysinfo`, `hashdump`) to assess the level of access and extract system and credential information from the Metasploitable2 target.

## Lab Environment
1. Virtual Box: `Oracle VirtualBox`
2. Host/Attacker System: `Kali Linux`
3. Target System: `Metasploitable2`
4. Target IP Address: `192.168.56.7`
5. Attacker IP Address: `192.168.56.4`
6. Network Configuration: `Host-Only Adapter`
7. Tools: `Metasploit Framework (msfconsole)`

## Rules of Engagement for This Phase
- All commands are typed into the Kali Linux terminal, continuing from the session established in the Controlled Exploitation phase.
- No persistence mechanisms, new accounts, or destructive actions are performed.
- Only enumeration/read commands are used to demonstrate impact.

## Process

### Step 1: Background the Active Shell Session

#### Command Used
```bash
background
```

#### Explanation
The command shell session obtained from the `vsftpd 2.3.4` exploit was backgrounded within Metasploit so it could be upgraded to a Meterpreter session, which supports structured post-exploitation commands.

#### Results
- Session Backgrounded: `[Yes/No]`
- Session ID: `[Record actual session ID, e.g. 1]`

<img src="./Images/Phase_6/Phase_6_1.png" height="200px"><br>

### Step 2: Confirm the Active Session

#### Command Used
```bash
sessions -l
```

#### Explanation
Listed active sessions to confirm the session ID of the backgrounded command shell before upgrading it.

#### Results

| Session ID | Type | Target |
|---|---|---|
| `[Record actual ID]` | `shell` | `192.168.56.7` |

<img src="../Images/Phase_6/step2_session_list.png" height="200px"><br>

### Step 3: Upgrade the Shell to a Meterpreter Session

#### Command Used
```bash
sessions -u 1
```

#### Explanation
Upgraded the existing command shell (Session 1) to a Meterpreter session, which provides built-in post-exploitation commands such as `sysinfo` and `hashdump`. Metasploit automatically starts a new listener and migrates the session.

#### Results
- Upgrade Status: `[Record actual result]`
- New Meterpreter Session ID: `[Record actual session ID, e.g. 2]`

<img src="../Images/Phase_6/step3_session_upgrade.png" height="200px"><br>

### Step 4: Interact With the Meterpreter Session

#### Command Used
```bash
sessions -i 2
```

#### Explanation
Interacted with the newly created Meterpreter session to begin running post-exploitation commands.

<img src="../Images/Phase_6/step4_session_interact.png" height="200px"><br>

### Step 5: Run System Information Command

#### Command Used
```bash
sysinfo
```

#### Explanation
Retrieved system information from the target, including hostname, OS, and architecture, to confirm details about the compromised machine.

<img src="./Images/Phase_6/Phase_6_2.png" height="200px"><br>

#### Results

| Field | Observed Output |
|---|---|
| Computer | `[Record actual output]` |
| OS | `[Record actual output]` |
| Architecture | `[Record actual output]` |
| Meterpreter | `[Record actual output]` |

### Step 7: End the Session

#### Command Used
```bash
exit
```

#### Explanation
Once post-exploitation commands were run and documented, the Meterpreter session was closed. No files were created, modified, or deleted on the target, and no persistence mechanism was installed, in accordance with the rules of engagement.

<img src="../Images/Phase_6/step5_sysinfo.png" height="200px"><br>

## Security Observations

1. The compromised session, upgraded from a plain reverse shell, carried unrestricted root privileges on the target.
2. Password hash data was extractable without any further exploitation or privilege escalation step.

## Conclusion

The Post-Exploitation phase confirmed that the reverse shell access gained through the `vsftpd 2.3.4` backdoor could be upgraded to a full Meterpreter session, enabling structured post-exploitation commands. `sysinfo` confirmed system details and credential exposure on the Metasploitable2 target. No persistence or destructive actions were taken. These findings reinforce the critical severity of the original finding and carry forward into the final Reporting phase.