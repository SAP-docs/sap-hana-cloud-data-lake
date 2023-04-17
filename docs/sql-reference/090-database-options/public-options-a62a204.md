<!-- loioa62a204d84f21015a1d6b0135fe7d082 -->

# PUBLIC Options

`PUBLIC` options can be set for a user, user extended role, or the PUBLIC role. They can be set for self or for another user or role.

Setting a `PUBLIC` option for the PUBLIC role sets the value for all users who do not already have the `PUBLIC` option set at the user level. Setting a `PUBLIC` option for a user or user-extended role overrides any value defined at the PUBLIC role level.

No system privilege is required to set a `PUBLIC` option for self, but does require the SET ANY CUSTOMER PUBLIC OPTION system privilege to set for another user, user-extended role, or PUBLIC role. `PUBLIC` options cannot be set for user-defined roles. `PUBLIC` database options take effect immediately. No shut down and restart of data lake Relational Engine is required for the change to take effect.

