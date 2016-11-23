# Syntax

`REDUCE` takes a single list as parameter.

The result of the call to `REDUCE` will be a single list containing *reduced* versions of all geo time series present in the input lists according to *partitions* defined by a list of *labels* and a *reducer* function.

## Format
```
[ [GTS] ... [GTS] [labels] reducer ] REDUCE
```

## Parameters
>`[GTS]`  
> One or several lists of geo time

>`[labels]`  
> A list of *labels* use for building partitions
> If an empty list is provided, use all *labels*.

>`reducer`  
> Function applied on each tick of each partition.  
> Available `reducer` are *reducer.sum*, *reducer.min*, *reducer.max* or *reducer.mean*

Don't hesitate to modify the parameters on the left terminal to experiment answers

~~~~

[
  '["60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFsB0N.4V.Q...LV71.gSEcZVJLV71vrNB44aFa.0Wk6sg7.........EjXkB1er4kPwN0WPw6bmY25_VAvnvyUtrFvItgHoC1kyqsnezoMrogUKztyEW69GuRGuZnhPxtDn32ktywfDv643dRykiQ4VFr341UDM7GuqsA4pv_gmMR6mAN7.F.rVI4v9V3..0Ns3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV719xgjTZVJLV71vrNB44a7a.0WZ6sg7.........EjXkB1er4kPwN0WPw3b8zvSMmvQUu_uuAtDd6dXF3E2vfjCfDYo41WhzqMyjf7ILmk8ekBeXW077emiMOi8lrBMtUPKVHr3dFurjYJRWacj9k6osBD73V3..0No3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VA99ffPH0GP.VAjSVkJLJXN.54NUXkV.........yyA.k9fRM0flV54fkLTQd6jtCyozzEqwnMMWuNZ02FqvvnPnIc6HxWy_tiwfDv348Zu7GiWnbhf7db9ML6q3nNDs.k0iUzPgiV...0NZ3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Vk4V.L.0g..0P.V71loyXH0GP.VAjSVkJLO1N.55FUXkV.........yyA.k9fRM0flV54fkTU9BBPL.jjE3F88jdRyIF_cPCWxhtbKzjD_YmhzEwyS1DLYokWp0NijRxZL39iEg6ZnFL.LdjYjtnbSnhD7CsRwSw0c.B.d1VNX.F..4YVG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71AhtiSZVJLV71vrNB44Yka.0W46sg7.........EjXkB1er4kPwN0WPw6bbVDGevIgjofCrpSqNgj3V7P5rMTQLP_CIs6Hx_ySdnPmeSk4.9tSMlq1....4WcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFsB0N.4V.Q...LV71.gSEcZVJLV71vrNB44aFa.0Wn6sg7.........EjXkB1er4kPwN0WPw6bmY25_VAvAzEr_OrNNYZ_c94WxxpaKjijJa10XK.yDVpMxqLAONG.ZWx1MourwxG5C_nu18hrKlxcRna5y4TFeHdrXIUb0CWWOAjY9tShkTAfM.1M6DKF9V3..0Ns3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.V9Y4hR1H0GP.VAjSVkJLK1N.56FUXkV.........yyA.k9fRM0flV54fkJz5qkaqYyozU4ntyr_DxwH.WcQSSthOoTZdJCfycxIwULJbhW0LtnmpZJr_AePsJCvoMjzv12uMQR6XuplkzcT6vih3eWsXt7r0.CBRX2u1vc2u1k2.ZoB5wV...0Nc3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Vk4V.L.0g..0P.VDDXiRLH0GP.VAjSVkJLKXN.55wUXkV.........yyA.k9fRM0flV54fkTU9BBPL.jgE8vONGVVZIF_cPCWxhtbKzgE6_QyUtrGEWEAGPNHuhlBnXYNckEZUdTQj9nil0ORykiNxS4wbJjJFFzkY_qr0sihRl8g2RIw.tz9GHyc....L9W3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VDDXiRLH0GP.VAjSVkJLFXN.54RUXkV.........yyA.k9fRM0flV54fkLTCWmZUjhhz1MnS9fRYP3d.FwEiiwqgx_z9IamlY01N1DLYokWpwzT0KD8HGmgPNQxYdvbrgGJ.DTTpVC7....L9W3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71AhtiSZVJLV71vrNB44Y.a.0W46sg7.........EjXkB1er4kPwN0WPw6bQehnYlIhjwnUKrOXXyM3V7P5rMTQLP_CIs6Hx_wyfjnxE9RQ.7KctKe1....4WcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72HqvPKZFJLV71vrNB44V7a.0V.4V.H..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71wnuPgZVJLV71vrNB44Vca.0W1x3..0HGVjOc..AKkwsn.LPceEyHYpkcxR9HGJ71.ixq20O4FV71vrNB4ZK1.VAjSVkLJJ71.ixq20Iza46fWGusJ4VcH..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VAiDpyqH0GP.VAjSVkJLT1N.55oUXkV.........yyA.k9fRM0flV54fkLUdyeriwUOUD.nKM_ORbGAFoA2vQYDfzGTGecUiuoFFU82o_MwIcMl1C39UvuLE9rwz8unDpAvavRFBkidJvidAnSx6iYhZpc0wH9ut..OLQ9Fm.F..4YcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2.k4V.L.0g..0P.VCbSkByH0GP.VAjSVkJLPXN.53sUXkV.........yyA.k9fRM0flV54fkQy.T8wVKziEn_BQqKIiIVlcPCWxhtaKrjFJ95rzZRiqNE4pAdApUUXswjUnb5s.ra.7yhc....LAW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VDDXiRLH0GP.VAjSVkJLFXN.54VUXkV.........yyA.k9fRM0flV54fkLTCWmZUjhhzQ8MQ3UXuSJd.FwEiiwqgxWybCf9drCLU1DLYokWptqu9hLgnsK869ldWUourBx1d.7C28dUH....4XcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71vYhUhZVJLV71vrNB44bVa.0X3.GyA1.........2vsg2.ehlR5j5.NLj0dnjbG6ixvAzaS2hEQLHQ3h2FgEhiBujxKzzvpX_GgWDWU7FsH8M9MKneo5a3iWXCfsUuNl2w98Zp67Qe16u3F8AjdJysnB3oAkKg.Ady00zSExY_ROiEMnp1jDA9rwzQr61t4k1qUMhmPV3..0Nu3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV724owzYZVJLV71vrNB44a7a.0WR6sg7.........EjXkB1er4kPwN0WPw5bzEqC3rjhjyOoDoxhO8gNoC1kyqsn9vbo41WhznJ_HaNCWm4WSG31HQuME_4eAuPtqEq2Z9yswjUnCYR.aVKp7Fc0...LCW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71vYhUhZVJLV71vrNB44bVa.0XM.GyA1.........2vsg2.ehlR5j5.NLj0OybufTvlx_wQqKIiuZhE25Wcq6qraMJ9_AQzahEhEALG2R66dPvavRHBcVokRJnteL1C1EvwULJbh_VWy1hzEwzdSg5hjiA9rwzQr61Qrmer7z0p9qttX6toUy4LrqbiULnt0kHzpzyySJcJQbaFvlLDcfgUrMk.vqDBd6c0...LDW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_.qJsCFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VAiDpyqH0GP.VAjSVkJLT1N.53VUXkV.........yyA.k9fRM0flV54fkLUdyeriwUQEsZnhPxtDb0YFoA2vQYBfeUFJ95rzYBSn4x.cRgqW4ko.BBMcNk70...LDW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71vYhUhZVJLV71vrNB44bVa.0Wj6sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlztfIvImpZLp9F3E2vfjCfEOUzTxQdoI8IcImXPJGy_DXOCOk508L4m5Ft6jd3z6a8YWqabgUGxTEs3EwFQdv9uvwzQnC2ORu.8UDm03m.F..4YcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72Ycfb4ZVJLV71vrNB44Z7a.0WH6sg7.........EjXkB1er4kPwN0WPw4bYNRd6vvQUnallI8175_XF3E2vfjCfAYc9K2Pzgj6_QyUtrFIJZxh5a6z0cJYgtRy0V.PJDKjmV...0Ne3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71clQM.ZVJLV71vrNB44_Fa.0Wr6sg7.........EjXkB1er4kPwN0WPw6bbVDGevIgjkVZyKvui5d9F3E2vfjCfEOUA1C.7WDWU7GsqNZhF1aND1sPcMvyEd.DrE9Sthv6_bx.wDCBvLjTIZIkqvLOT2lrNTdQkq5cxf91gEoFxk7.YsTEzE7....L903.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VAiDpyqH0GP.VAjSVkJLT1N.57s06sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlzmVpUpzOXHpI.WcPShxhOfMz98FrjSUzzZFc6oNYtCKTK_ntykM0pkROR08SEPNytuaCQ1fr3Ek7VHIUHtxkawh_Lv2sDWSiwx2SnGU57Y5t44ozQb_1zaGIiPgjhF1rUG0tMEu5oF0RbgEdRV3..0Nu3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72Ycfb4ZVJLV71vrNB44Zca.0W86sg7.........EjXkB1er4kPwN0WPw5bXmTbq0IOUtrPm9OmKrxXF3E2vfjCfAHXdo0dyuwtrRt.9wbMvklqB.2iBsecmV...0Ne3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72Ycfb4ZVJLV71vrNB44Zca.0WJ6sg7.........EjXkB1er4kPwN0WPw5bXmTbq0IOUz5xx66_vyRI.lcPShxhOgK4Is6Hx_xDQA5B33VXd8ukDUEr_F5C7_xz5SVW.03wzDUH....4XcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.V9Y4hR1H0GP.VAjSVkJLK1N.56kUXkV.........yyA.k9fRM0flV54fkTTT.t5fhDkzbCWX5H5FC1LVcL6rrLOLykwUKztybhBx3Rd6dy6eEZfCrpSqNVhWSRtI5x_Jva99wsLlH3kiFSYvo6qSHCK2W2mMQR6XupmNyiGq0Ati_HCcAxFU.8oGIsvm....4XVG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VBMInyDH0GP.VAjSVkJLRXN.54cUXkV.........yyA.k9fRM0flV54fkPUwzNoITyoz9WmOjUGlmBH.WcQSSthOmPLbF5bvYwtI5x_Jva99LuS3mPnWk0HMafyjvBFLHiob_VN.mw0Rak70...LCW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71AhtiSZVJLV71vrNB44Yka.0W46sg7.........EjXkB1er4kPwN0WPw3b8zvSMmvQUtLPjuzgl8P8.FoCiywqgp9QbV9_vQwuIqpZJvZA..EOAYD1....4WcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.V7fqmxuH0GP.VAjSVkJLP1N.553UXkV.........yyA.k9fRM0flV54fkHRbzhpUAhhz3P_uuAtDO58.FwEiiwqgiDVdJCfyHtIB5Vt2SJAeRTjrjUGltTzbODjz2CPTHvlx9bUpdTQjFrRz.AmBQTs9.F..4YFG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Zk4V.L.0g..0P.V7fqmxuH0GP.VAjSVkJLRXN.58J06sg7.........EjXkB1er4kPwN0WPw6Ea4L5hLjgEofCrpSqNgiJV7P5rMTQLTozgebRpOSPVD1fjPmswjUAG1VU7PsEobVHkOyNJQG0sHWB6POuZEHGDTYmaDcH62jCjNz2yGyDn4vuDEV6QjMPI2mTiy7klRMPVI8TuEv1OIy5zVwUKztybhDCQWs._YPkjZ70...LC03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV724owzYZVJLV71vrNB44a7a.0Vu6sg7.........EjXkB1er4kPwN0WPw5bzEqC3rjhbuwIeMfcjatXF3E2vfjCfBD40V1VhjVNuV...0Nq3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.V9Y4hR1H0GP.VAjSVkJLK1N.55sUXkV.........yyA.k9fRM0flV54fkJz5qkaqYyozCv9drCLMbWAFoA2vQYDfzTTKjtzbSAgVy8Ry.ZKm8oAtW5X3Ed.lnhBklJxggNkFH3Ak2zM6P6kxYD2E074OiBkWrbu7ik5wWERmwV...0Nc3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.V7iratqH0GP.VAjSVkJLH1N.537UXkV.........yyA.k9fRM0flV54fkTSierDE4DozDZxhO4DtDn5VcL6rrLOLPhCIcAIxltliZ3o.8SJl777....L5W3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71mXeuqZVJLV71vrNB44YVa.0W26sg7.........EjXkB1er4kPwN0WPw4bauGvyIUhjnPmeSnK_tsNoC1kyqsnuo2GJu1ozKUbeH.M.F.MFusqeV...0NZ3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVkB0N.4V.Q...LV72OrR2EZVJLV71vrNB44aca.0W66sg7.........EjXkB1er4kPwN0WPw5zV6XU74UvAqJbh_W513kBP5YNUQTO_Svo41WhzqMyEd0AHCR6RIw.KtNRXSc....LAW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VAiDpyqH0GP.VAjSVkJLT1N.56cUXkV.........yyA.k9fRM0flV54fkPRvtoGvjTkzzruToyowQJd.FwEiiwqgx_w3ZbkjUKkp3Rd6X1gRaQroRFX1fr8MMqfyEVIUha2lSHtQa2t1C5tnD.nKM_OR8PHTL6gkx9EvxnD7DvJGdnk0yk17m1vwJV3..0Nu3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VAiDpyqH0GP.VAjSVkJLT1N.58706sg7.........EjXkB1er4kPwN0WPw5bDyS3TvrgEofCrpSqNgiJV7P5rMTQLTozwcLlH3kibFY_kqX3jCfAXXhzjm2syX.2Ie9flxIbEALGITJTVWwWZDGvuGCiRv_g1lOUtw8h6gHSiCIYKXTJCvrMzntiRx_JvidAAH2cbkxzEqxnMMVPMGs.VXNot570...LDW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71vYhUhZVJLV71vrNB44bVa.0WI6sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlUrtgyUitarFb0YFovAvQn3chTVeJhbyu9wvJjiNSmUeTeSnK_tezYxfiVh3.foTnhFc0...LDW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2.k4V.L.0g..0P.VCbSkByH0GP.VAjSVkJLPXN.53JUXkV.........yyA.k9fRM0flV54fkQy.T8wVKzjEjtzbS2hEalYFoA2vQYEfN9TbF5bvntRyfjnxE0R.A_OxxC7....LAW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VAiDpyqH0GP.VAjSVkJLT1N.57706sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlzznvTJurwvFd.FoCiywqgxdz3JYmjUGlpJFc6m3igsQ2JDo_VexmKpxezYs3rvOVwMJiLtVyIEp.JpUyUctQrY71PEC_MDv.K.yl6pqT3.rM2zJrdfZFTsap0k.iaIUiJV3..0Nu3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72Ycfb4ZVJLV71vrNB44aFa.0WB6sg7.........EjXkB1er4kPwN0WPw6jRsovC1vOUtazfyn34gi8.FoCiywqgy9Xdo0dymx.lG31HNIJJth5q.xlAk0KLVjOmV...0Ne3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFtB0N.4V.Q...LV719xgjTZVJLV71vrNB44aVa.0Wg6sg7.........EjXkB1er4kPwN0WPw6Ea4L5hLjgjvmSa45oFM4XF3E2vfjCfDYo41WhzpLgMOi8lkj0huw0uXn5dFyrDJ2Q47vB7KNUQbD7glyWMafyjf7ILl0wcQndjUvr.JVCdj.H.F..4YFG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71clQM.ZVJLV71vrNB44_Fa.0Wu6sg7.........EjXkB1er4kPwN0WPw4Elhg8hczhjuYRpOTPjqx9F3E2vfjCfEOUU1xxMEbvDN8USa9AONI.G1XU37rFCrwUH1TaTAUnp3NqKFHzMOi8lrBMVWxbP_znSX91jmEkSPjR2ZAasrN6lEo.Ljk2Djc....L903.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71AhtiSZVJLV71vrNB44Y.a.0W26sg7.........EjXkB1er4kPwN0WPw6bQehnYlIhjyOoDoxhO8gNoC1kyqsn9vMd9K2PzXjF3dLvyV14yi0AVV...0NP3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV71Mzf9FZFJLV71vrNB44V7a.0V.4V.H..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VAiDpyqH0GP.VAjSVkJLT1N.58B06sg7.........EjXkB1er4kPwN0WPw4buUehvj6q6uMavmgvgLKXF3E2vfjCf4DVhEp6yter3nD93MlxZB9I1Asl512spX_GBagsNDOVadUVq5biUGn00mgrFj.nXYNc68a28ay7s3R78E_TycGiEeNxn_BQqKIi7jWeAmiizEq1HlyaUhIk78N5.AsPO50P.F..4YcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VDDXiRLH0GP.VAjSVkJLJXN.54VUXkV.........yyA.k9fRM0flV54fkPTA8uUN4C_zyAYmxzDRvcZ02FqvvnPnIc6HxWy_tiwfDv348csdvnmpZJr_AfcwgIFWTsYL2rJz..wr9_EP....4XcG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71mXeuqZVJLV71vrNB44_7a.0WK6sg7.........EjXkB1er4kPwN0WPw4bauGvyIUhjzWTyfYmxzD8.FoCiywqgou0ojOUtiwfDv643XODX3Qc.qe933VXKWxWwm2i..2kBP_7iV...0NZ3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_.qJsCFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VDucVUeG0GP.VAjSVkJL.XN.50foF..47yV9YR..hM2vPtu9YiBztVl8i_spElN13V.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV71vYhUhZVJLV71vrNB44bVa.0WI6sg7.........EjXkB1er4kPwN0WPw5bDyS3TvrgblxQzbvi8hq8.FoCiywqgp9AbV9_vOziXYDpfr_6gftb9bUpdTQjcvPvN2F.4_G5jkc0...LDW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VDDXiRLH0GP.VAjSVkJLOXN.53oUXkV.........yyA.k9fRM0flV54fkTzgTKpxYyozHgrUKrOXmwH.WcQSSthORS4IcAIxGyTdYLkeSkaddnPCg0zXMV.P1a0WmV...0Ne3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFtB0N.4V.Q...LV724owzYZVJLV71vrNB44bFa.0XQ.GyA1.........2vsg2.ehlR5j5.NLj0ntWKWfKfvAx3mPnWB4HU5C2FgEhiBygJ95rzONE1ZS_A6qD9vwaeyr_Q5R4zai2NPTs2JoT7WijvmWU57Y5t456Dnxh94tsa7EVrlSepaMWkujymlI817BZEJlncuD2jtl4wcDiwYuoVu8sjRPQqCLwbNccMVF8X5Qft.7AfLfh9.F..4YNG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VBMInyDH0GP.VAjSVkJLRXN.55NUXkV.........yyA.k9fRM0flV54fkPUwzNoITyozzruToyowQL8.FwEiiwqgtC8IcAIx_mIUHlxMzg3J0kbzUcsdfb8MMqfyEZfhlnGM.DHFKQYgFNWQGV0KMVN.ftxzIGc0...LCW3.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.V9Y4hR1H0GP.VAjSVkJLM1N.55RUXkV.........yyA.k9fRM0flV54fkHRbzhpUAhhzyAYmxzDRvcZ02FqvvnPnchCIcAIxGubtywdDQB5_2_DxwxG5CdLvaD81TSCvzTwYy4mq0NijRl3m4uRxJER2..kGx8vP....4XVG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VDDXiRLH0GP.VAjSVkJLOXN.53oUXkV.........yyA.k9fRM0flV54fkTxnYIgoAh_z_8ezfyn3_cZ02FqvvnPnchCIcAIxGyTdYLkeSr5dcnLCR.U3jF.waZzTmV...0Ne3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV725_8yXZVJLV71vrNB44VVa.0Vux3..0HGBbw9V.AKkyF6QN2rYEyHYpkcxR9HGJ71.ixq20O4FV71vrNB4_41.VAjSVkJztWGusJTi40N73V.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72Ycfb4ZVJLV71vrNB44_Na.0WB6sg7.........EjXkB1er4kPwN0WPw6jv6_SUNzhjwnUKrOXXyM3V7P5rMTQLM6GJu1ozGTVsVX083AeeJoYv7Ts4k.nuBnpmV...0Ne3F."]'
  JSON->

  UNWRAP

  bucketizer.mean
  0
  604800000000
  0
] BUCKETIZE
'type' 1 ->LIST
reducer.min
3 ->LIST
REDUCE