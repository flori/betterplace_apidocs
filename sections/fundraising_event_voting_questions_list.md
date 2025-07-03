
# Fundraising Event Voting Questions List

```Cirru
GET https://api.betterplace.org/de/api_v4/fundraising_events/1/stream_question.json
```

The voting question currently shown in the streamer widget.

**This is a temporary feature on this api. Do not use!.**


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">fundraising_event_id</th>
    <td><code>1</code></td>
    <td>yes</td>
<td>

Fundraising Event id as an integer number.

</td>
  </tr>
</table>


## Response Attributes

  <th colspan="4">No response example defined</th>
</table>

## Response Links

<table>
  <tr>
    <th>Linkname</th>
    <th>Description</th>
  </tr>
  <th colspan="2">No response example defined</th>
</table>

## Response Example

```json
{
  "id": 20,
  "text": "Charakterwahl für Super Smash Bros. Ultimate!",
  "aasm_state": "finished",
  "fundraising_event_id": 49833,
  "created_at": "2025-06-26T12:46:24+02:00",
  "updated_at": "2025-06-28T18:31:58+02:00",
  "finished_at": "2025-06-28T18:31:58+02:00"
}
```

