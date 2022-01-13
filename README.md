# Tutorial and Script Dedicated for Newbie Develepor
All content in this repo is free. Everyone is allowed to use, copy, modify, merge, publish, distribute, sublicense, and/or sell it with and/or without any permission.

### Camera follow player
public class FollowPlayer : MonoBehaviour
{
    public Transform player;
    public Vector3 offset;

    // Update is called once per frame
    void Update()
    {
        transform.position = player.position + offset;
    }
}
