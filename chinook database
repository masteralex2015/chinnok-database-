-- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';

-- -----------------------------------------------------
-- Schema mydb
-- -----------------------------------------------------
-- -----------------------------------------------------
-- Schema chinook_aleksis
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Schema chinook_aleksis
-- -----------------------------------------------------
DROP DATABASE if exists chinook_aleksis;
CREATE SCHEMA IF NOT EXISTS `chinook_aleksis` DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci ;
USE `chinook_aleksis` ;

-- -----------------------------------------------------
-- Table `chinook_aleksis`.`artists`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`artists` (
  `ArtistId` INT NOT NULL,
  `Name` VARCHAR(120) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  PRIMARY KEY (`ArtistId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = UTF8MB4_0900_ai_ci
COMMENT = '	';


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`albums`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`albums` (
  `AlbumId` INT NOT NULL,
  `Title` VARCHAR(160) CHARACTER SET 'utf8' NOT NULL,
  `ArtistId` INT NOT NULL,
  PRIMARY KEY (`AlbumId`),
  INDEX `ArtistId_idx` (`ArtistId` ASC) VISIBLE,
  CONSTRAINT `ArtistId`
    FOREIGN KEY (`ArtistId`)
    REFERENCES `chinook_aleksis`.`artists` (`ArtistId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`employees`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`employees` (
  `EmployeeId` INT NOT NULL,
  `LastName` VARCHAR(20) CHARACTER SET 'utf8' NOT NULL,
  `FirstName` VARCHAR(20) CHARACTER SET 'utf8' NOT NULL,
  `Title` VARCHAR(30) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `ReportsTo` INT NULL DEFAULT NULL,
  `BirthDate` DATETIME NULL DEFAULT NULL,
  `HireDate` DATETIME NULL DEFAULT NULL,
  `Address` VARCHAR(70) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `City` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `State` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Country` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `PostalCode` VARCHAR(10) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Phone` VARCHAR(24) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Fax` VARCHAR(24) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Email` VARCHAR(60) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  INDEX `EmployeeId` (`EmployeeId` ASC) VISIBLE,
  INDEX `EmployeesId_idx` (`ReportsTo` ASC) VISIBLE,
  CONSTRAINT `EmployeesId`
    FOREIGN KEY (`ReportsTo`)
    REFERENCES `chinook_aleksis`.`employees` (`EmployeeId`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`customers`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`customers` (
  `CustomerId` INT NOT NULL,
  `FirstName` VARCHAR(40) CHARACTER SET 'utf8' NOT NULL,
  `LastName` VARCHAR(20) CHARACTER SET 'utf8' NOT NULL,
  `Company` VARCHAR(80) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Address` VARCHAR(70) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `City` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `State` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Country` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `PostalCode` VARCHAR(10) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Phone` VARCHAR(24) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Fax` VARCHAR(24) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Email` VARCHAR(60) NOT NULL,
  `SupportRepId` INT NULL DEFAULT NULL,
  PRIMARY KEY (`CustomerId`),
  INDEX `SupportRepId_idx` (`SupportRepId` ASC) VISIBLE,
  CONSTRAINT `SupportRepId`
    FOREIGN KEY (`SupportRepId`)
    REFERENCES `chinook_aleksis`.`employees` (`EmployeeId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`genres`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`genres` (
  `GenreId` INT NOT NULL,
  `Name` VARCHAR(120) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  PRIMARY KEY (`GenreId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`invoices`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`invoices` (
  `InvoiceId` INT NOT NULL,
  `CustomerId` INT NOT NULL,
  `InvoiceDate` DATETIME NOT NULL,
  `BillingAddress` VARCHAR(70) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `BillingCity` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `BillingState` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `BillingCountry` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `BillingPostalCode` VARCHAR(40) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Total` DECIMAL(10,0) NOT NULL,
  PRIMARY KEY (`InvoiceId`),
  INDEX `Invoices_idx` (`CustomerId` ASC) VISIBLE,
  CONSTRAINT `Invoices`
    FOREIGN KEY (`CustomerId`)
    REFERENCES `chinook_aleksis`.`customers` (`CustomerId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`invoice_items`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`invoice_items` (
  `InvoiceLineId` INT NOT NULL AUTO_INCREMENT,
  `InvoiceId` INT NOT NULL,
  `TrackId` INT NOT NULL,
  `UnitPrice` DECIMAL(10,2) NOT NULL,
  `Quantity` INT NOT NULL,
  PRIMARY KEY (`InvoiceLineId`),
  INDEX `IFK_InvoiceLineInvoiceId` (`InvoiceId` ASC) VISIBLE,
  INDEX `IFK_InvoiceLineTrackId` (`TrackId` ASC) VISIBLE,
  CONSTRAINT `invoice_items_ibfk_1`
    FOREIGN KEY (`InvoiceId`)
    REFERENCES `chinook_aleksis`.`invoices` (`InvoiceId`),
  CONSTRAINT `invoice_items_ibfk_2`
    FOREIGN KEY (`TrackId`)
    REFERENCES `chinook_aleksis`.`tracks` (`TrackId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;

-- -----------------------------------------------------
-- Table `chinook_aleksis`.`media_types`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`media_types` (
  `MediaTypeId` INT NOT NULL,
  `Name` VARCHAR(120) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  PRIMARY KEY (`MediaTypeId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`playlists`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`playlists` (
  `PlaylistId` INT NOT NULL,
  `Name` VARCHAR(120) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  PRIMARY KEY (`PlaylistId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`tracks`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`tracks` (
  `TrackId` INT NOT NULL,
  `Name` VARCHAR(200) CHARACTER SET 'utf8' NOT NULL,
  `AlbumId` INT NULL DEFAULT NULL,
  `MediaTypeId` INT NOT NULL,
  `GenreId` INT NULL DEFAULT NULL,
  `Composer` VARCHAR(120) CHARACTER SET 'utf8' NULL DEFAULT NULL,
  `Miliseconds` INT NOT NULL,
  `Bytes` INT NULL DEFAULT NULL,
  `UnitPrice` DECIMAL(10,0) NOT NULL,
  PRIMARY KEY (`TrackId`),
  INDEX `MediaTypeId_idx` (`MediaTypeId` ASC) VISIBLE,
  INDEX `GenreId_idx` (`GenreId` ASC) VISIBLE,
  INDEX `AlbumId_idx` (`AlbumId` ASC) VISIBLE,
  CONSTRAINT `AlbumId`
    FOREIGN KEY (`AlbumId`)
    REFERENCES `chinook_aleksis`.`albums` (`AlbumId`),
  CONSTRAINT `GenreId`
    FOREIGN KEY (`GenreId`)
    REFERENCES `chinook_aleksis`.`genres` (`GenreId`),
  CONSTRAINT `MediaTypeId`
    FOREIGN KEY (`MediaTypeId`)
    REFERENCES `chinook_aleksis`.`media_types` (`MediaTypeId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `chinook_aleksis`.`playlist_track`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `chinook_aleksis`.`playlist_track` (
  `PlaylistId` INT NOT NULL,
  `trackId` INT NOT NULL,
  PRIMARY KEY (`PlaylistId`, `trackId`),
  INDEX `TrackId_idx` (`trackId` ASC) VISIBLE,
  CONSTRAINT `PlaylistId`
    FOREIGN KEY (`PlaylistId`)
    REFERENCES `chinook_aleksis`.`playlists` (`PlaylistId`),
  CONSTRAINT `TrackId`
    FOREIGN KEY (`trackId`)
    REFERENCES `chinook_aleksis`.`tracks` (`TrackId`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;

ALTER TABLE invoice_items
ADD FOREIGN KEY (TrackId) REFERENCES tracks(TrackID);
ALTER TABLE invoice_items
ADD FOREIGN KEY (TrackId) REFERENCES tracks(TrackID);

SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
