# `arqc`

A wrapper for the [`arqc`](https://www.arqbackup.com/documentation/arq7/English.lproj/arqc.html) command.

## TypeScript package

This package is published as TypeScript source files. You will need to use a compatible bundler (such as `esbuild`) or runtime (such as `bun`) to import this code.

## API

````ts
interface BackupActivityJSON {
    aborted: boolean;
    abortReason?: string;
    activityLogPath: string;
    backupPlanDbId: number;
    backupSetUUID: string;
    countOfBytes: number;
    countOfBytesUploaded: number;
    countOfFiles: number;
    countOfFilesUploaded: number;
    createdTime: number;
    dataVersion: number;
    errorCount: number;
    finishedTime: number;
    message: string;
    subType: string;
    type: string;
    updatedTime: number;
    uuid: string;
}
interface ArqBackupPlanConfig {
    backupSetUUID: string;
    name?: string;
    storageLocation?: string;
}
declare class ArqBackupPlan {
    #private;
    config: ArqBackupPlanConfig;
    constructor(config: ArqBackupPlanConfig);
    latestBackupActivityJSON(): Promise<BackupActivityJSON>;
    latestBackupActivityLog(): Promise<string>;
    wasLatestBackupSuccessful(): Promise<boolean>;
    start(): Promise<void>;
    stop(): Promise<void>;
}

declare function acceptLicenseAgreement(): Promise<void>;
declare function pauseBackups(minutes: number): Promise<void>;
declare function resumeBackups(): Promise<void>;
declare function listBackupPlans(): Promise<ArqBackupPlan[]>;

declare function setArqcCommandPath(newPath: string): void;

export { ArqBackupPlan, type ArqBackupPlanConfig, type BackupActivityJSON, acceptLicenseAgreement, listBackupPlans, pauseBackups, resumeBackups, setArqcCommandPath };
````
