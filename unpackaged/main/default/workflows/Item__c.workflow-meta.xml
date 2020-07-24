<?xml version="1.0" encoding="utf-8"?><Workflow xmlns="http://soap.sforce.com/2006/04/metadata">
    <alerts>
        <fullName>External_New_Item_Notification</fullName>
        <description>External New Item Notification</description>
        <protected>false</protected>
        <recipients>
            <field>Bluewave_Assignee_Email__c</field>
            <type>email</type>
        </recipients>
        <senderType>CurrentUser</senderType>
        <template>Bluewave_Tracker_Emails/New_Item</template>
    </alerts>
    <alerts>
        <fullName>Notify_Bluewave</fullName>
        <description>Notify Bluewave</description>
        <protected>false</protected>
        <recipients>
            <field>Bluewave_Assignee_Email__c</field>
            <type>email</type>
        </recipients>
        <senderType>CurrentUser</senderType>
        <template>Bluewave_Tracker_Emails/Item_Assigned_to_Bluewave</template>
    </alerts>
    <alerts>
        <fullName>Notify_Internal_Owner</fullName>
        <description>Notify Internal Owner</description>
        <protected>false</protected>
        <recipients>
            <field>Internal_Owner__c</field>
            <type>userLookup</type>
        </recipients>
        <senderType>CurrentUser</senderType>
        <template>Bluewave_Tracker_Emails/Item_Assigned_to_Customer</template>
    </alerts>
    <fieldUpdates>
        <fullName>Item_Status_to_Under_Review</fullName>
        <field>Status__c</field>
        <literalValue>Under Review</literalValue>
        <name>Item Status to Under Review</name>
        <notifyAssignee>false</notifyAssignee>
        <operation>Literal</operation>
        <protected>false</protected>
    </fieldUpdates>
    <fieldUpdates>
        <fullName>Set_Project_Mailbox</fullName>
        <field>Project_Mailbox__c</field>
        <formula>Project_Mailbox__c</formula>
        <name>Set Project Mailbox</name>
        <notifyAssignee>false</notifyAssignee>
        <operation>Formula</operation>
        <protected>false</protected>
    </fieldUpdates>
    <rules>
        <fullName>Bluewave Assignee Identified</fullName>
        <actions>
            <name>Item_Status_to_Under_Review</name>
            <type>FieldUpdate</type>
        </actions>
        <active>false</active>
        <criteriaItems>
            <field>Item__c.Bluewave_Assignee__c</field>
            <operation>notEqual</operation>
        </criteriaItems>
        <criteriaItems>
            <field>Item__c.Status__c</field>
            <operation>equals</operation>
            <value>New</value>
        </criteriaItems>
        <triggerType>onCreateOrTriggeringUpdate</triggerType>
    </rules>
    <rules>
        <fullName>Send Email Notification to Bluewave Assignee</fullName>
        <actions>
            <name>Notify_Bluewave</name>
            <type>Alert</type>
        </actions>
        <active>false</active>
        <criteriaItems>
            <field>Item__c.Bluewave_Assignee_Email__c</field>
            <operation>notEqual</operation>
        </criteriaItems>
        <criteriaItems>
            <field>Item__c.Status__c</field>
            <operation>equals</operation>
            <value>Awaiting Bluewave</value>
        </criteriaItems>
        <triggerType>onCreateOrTriggeringUpdate</triggerType>
    </rules>
    <rules>
        <fullName>Send Email Notification to Bluewave Customer</fullName>
        <actions>
            <name>Notify_Internal_Owner</name>
            <type>Alert</type>
        </actions>
        <active>false</active>
        <criteriaItems>
            <field>Item__c.Status__c</field>
            <operation>equals</operation>
            <value>Awaiting Customer</value>
        </criteriaItems>
        <triggerType>onCreateOrTriggeringUpdate</triggerType>
    </rules>
    <rules>
        <fullName>Send New Item Notification Externally</fullName>
        <actions>
            <name>External_New_Item_Notification</name>
            <type>Alert</type>
        </actions>
        <active>false</active>
        <formula>True</formula>
        <triggerType>onCreateOnly</triggerType>
    </rules>
    <rules>
        <fullName>Set Project Mailbox on Item</fullName>
        <actions>
            <name>Set_Project_Mailbox</name>
            <type>FieldUpdate</type>
        </actions>
        <active>true</active>
        <criteriaItems>
            <field>Item__c.Project_Mailbox__c</field>
            <operation>notEqual</operation>
        </criteriaItems>
        <triggerType>onCreateOnly</triggerType>
    </rules>
</Workflow>
