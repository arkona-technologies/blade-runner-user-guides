# RTP Transmitter

## Video

### Prerequesistes

- PTP-Clock is either Calibrated or in Freerun
- Genlock is Calibrated
- Some Video Source is present (e.g.: Signal Generator)

### Setup

To create a Video Transmitter, we first need to create a hosting session to host our video transmitter. We can do so via the Advanced UI, by clicking `+` under `r_t_p_transmitter.sessions` or via VAPI:

```typescript
await vm.r_t_p_transmitter.sessions.create_row();
```

Next, assign it either a primary or a primary and secondary interface, thereby enabling `2022-7`-redundancy.
To assign primary/secondary interfaces navigate to `r_t_p_transmitter.sessions[<INDEX>].intefaces` assign interfaces by opening the associated drop-down menu and selecting the desired interface. And with that our hosting session is ready to go!

Next, we'll create a fresh `video_transmitter` by navigating to `r_t_p_transmitter.video_transmitters` and clicking the `+` symbol to the right. This behaves analogous to creating a session (or any other kind of `nambed table` for that matter).
Assign the transmitter a `hosting_session` by selecting our freshly created session in the dropdown-menu at `r_t_p_transmitter.video_transmitters[<INDEX>].generic.hosting_session`.

`video_transmitters` come up configured as 3G capable `2110-20` Transmitters. To change the transmitters `transport_format` navigate to `r_t_p_transmitter.video_transmitters[<INDEX>].configuration.transport_format` and select whatever transport format you desire. **NOTE:** Make sure to submit your changes by pressing the upwards pointing arrow symbol.
When using `2022-6` you may configure embedded audio under `r_t_p_transmitter.video_transmitters[<INDEX>].configuration.embedded_audio` and set it's audio source under `r_t_p_transmitter.video_transmitters[<INDEX>].configuration.a_src`. For Transmitters using `2110-40` to transmit metadata you may configure timecode, vanc, smpte-352 override under `r_t_p_transmitter.video_transmitters[<INDEX>].configuration.vanc`.

Depending on your use-case and your desired video standard, you may need to change the transmitters `constraints`. These can be used to limit the video*transmitter to either only transmit up to a certain bandwidth (e.g. `b3_0Gb` would allow every video_standard up to **HD1080p60**) or a certain video standard. Navigate to `r_t_p_transmitter.video_transmitters[<INDEX>].constraints` and either specify a concrete video standard or an upper limit. _NOTE:_ Specific video standards will overwrite a bandwidth setting (e.g.: `max_bandwidth` set to `b12_0Gb` and standard set to `HD1080p50` would only allow `HD1080p50`).

Next we'll assign the transmitter a video source by selecting the desired video-essence under `r_t_p_transmitter.video_transmitters[<INDEX>].v_src`.

To configure Mutlicast Addresses, navigate to `r_t_p_transmitter.video_transmitters[<INDEX>].generic.ip_configuration`. Depending on whether 2110-40 is present or 2022-7 is being used you will need to assign mutlicast destination addresses for both media/meta and primary/secondary by entering a valid mutlicast address aswell as port into the respective `dst_address` field. For example, to set a video_transmitters primary media destination ip we'd enter `239.1.2.3:50020` into `r_t_p_transmitter.video_transmitters[<INDEX>].generic.ip_configuration.media.primary.dst_address`. _NOTE:_ Make sure to always confirm your entered commands by pressing `Enter` or `Shift-Enter`.

We may now activate the transmitter by activating it's hosting_session. Navigate to `r_t_p_transmitter.sessions[<INDEX>].acitve` and set it to `true`.

